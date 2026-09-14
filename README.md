import 'package:flutter/material.dart';
import 'package:google_sign_in/google_sign_in.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'cloud_manager.dart';
import '../../core/app_cleaner.dart';
import '../debug/debug_manager.dart';

class AuthService with ChangeNotifier {
  late final CloudManager cloudManager;

  static const String _clientId =
      '1021298502273-bdsucooa24a2pfdtckcicnq98o929jj2.apps.googleusercontent.com';

  final GoogleSignIn _googleSignIn = GoogleSignIn(
    clientId: _clientId,
    scopes: ['email', 'profile', 'openid'],
  );

  // 🔹 AppCleaner کے لیے گیٹر
  GoogleSignIn get googleSignInInstance => _googleSignIn;

  GoogleSignInAccount? currentUser;

  String? cachedEmail;
  String? cachedName;
  String? cachedPhoto;
  String? cachedId;

  AuthService() {
    cloudManager = CloudManager(authService: this);

    // 🔹 یہاں AppCleaner کو اپنا ریفرنس پاس کر رہے ہیں تاکہ لنک جڑ جائے
    AppCleaner.setAuthService(this);

    _loadCachedUser();
  }

  Future<void> _loadCachedUser() async {
    final prefs = await SharedPreferences.getInstance();
    cachedEmail = prefs.getString('user_email');
    cachedName = prefs.getString('user_name');
    cachedPhoto = prefs.getString('user_photo');
    cachedId = prefs.getString('user_id');

    if (cachedEmail != null) {
      DebugManager.instance.log('📦 لوکل کیش سے یوزر لوڈ ہو گیا: $cachedEmail');
      notifyListeners();
    }
  }

  Future<GoogleSignInAccount?> getUser() async {
    if (currentUser != null) return currentUser;
    try {
      DebugManager.instance.log('🔄 سائلنٹ سائن ان کی کوشش کی جا رہی ہے...');
      currentUser = await _googleSignIn.signInSilently();
      if (currentUser != null) {
        DebugManager.instance.log('✅ سائلنٹ سائن ان کامیاب: ${currentUser!.email}');
        await _saveUserToPrefs(currentUser!);
        await _syncUserWithCloud(currentUser!);
        notifyListeners();
      }
    } catch (e) {
      DebugManager.instance.log('❌ Silent Sign-In Error: $e');
      debugPrint("Silent Sign-In Error: $e");
    }
    return currentUser;
  }

  Future<void> loginWithGoogle() async {
    try {
      DebugManager.instance.log('🌐 گوگل لاگ ان پاپ اپ کھولا جا رہا ہے...');
      final user = await _googleSignIn.signIn();
      if (user != null) {
        currentUser = user;
        DebugManager.instance.log('✅ گوگل لاگ ان کامیاب: ${user.email}');

        await _saveUserToPrefs(user);
        await _syncUserWithCloud(user);

        notifyListeners();
      } else {
        DebugManager.instance.log('⚠️ یوزر نے گوگل لاگ ان کینسل کر دیا');
      }
    } catch (e) {
      DebugManager.instance.log('❌ Login Error: $e');
      rethrow;
    }
  }

  Future<void> _saveUserToPrefs(GoogleSignInAccount user) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setBool('is_logged_in', true);
    await prefs.setString('user_email', user.email);
    await prefs.setString('user_name', user.displayName ?? '');
    await prefs.setString('user_photo', user.photoUrl ?? '');
    await prefs.setString('user_id', user.id);

    cachedEmail = user.email;
    cachedName = user.displayName;
    cachedPhoto = user.photoUrl;
    cachedId = user.id;
    DebugManager.instance.log('💾 یوزر کا ڈیٹا لوکل SharedPreferences میں محفوظ ہو گیا');
  }

  Future<void> logout() async {
    try {
      DebugManager.instance.log('🚪 لاگ آؤٹ اور ڈیٹا صفائی کا عمل شروع...');
      final prefs = await SharedPreferences.getInstance();

      await prefs.remove('is_logged_in');
      await prefs.remove('user_email');
      await prefs.remove('user_name');
      await prefs.remove('user_photo');
      await prefs.remove('user_id');

      cachedEmail = null;
      cachedName = null;
      cachedPhoto = null;
      cachedId = null;

      // 🔹 یہ ایپ کلینر کو کال کرے گا جو ری سٹارٹ سے پہلے گوگل سائن آؤٹ بھی خود کر دے گا
      await AppCleaner.clearAll();

      currentUser = null;

      DebugManager.instance.log('✅ یوزر سائن آؤٹ اور تمام کیش کامیابی سے صاف ہو گئی');
      notifyListeners();
    } catch (e) {
      DebugManager.instance.log('❌ Logout Error: $e');
    }
  }

  Future<bool> isLoggedIn() async {
    final prefs = await SharedPreferences.getInstance();
    return prefs.getBool('is_logged_in') ?? false;
  }

  Future<String?> getIdToken() async {
    try {
      final user = currentUser ?? await _googleSignIn.signInSilently();
      if (user == null) return null;

      final authentication = await user.authentication;
      return authentication.idToken;
    } catch (e) {
      DebugManager.instance.log('❌ Get ID Token Error: $e');
      return null;
    }
  }

  Future<void> _syncUserWithCloud(GoogleSignInAccount user) async {
    try {
      DebugManager.instance.log('☁️ کلاؤڈ ورکر کے ساتھ یوزر سنک ہو رہا ہے...');
      final result = await cloudManager.callFunction({
        'action': 'sync_user',
      });
      DebugManager.instance.log('✅ کلاؤڈ سنک کامیاب: $result');
    } catch (e) {
      DebugManager.instance.log('❌ Cloud Sync Error: $e');
    }
  }
}