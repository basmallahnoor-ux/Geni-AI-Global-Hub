<!DOCTYPE html>
<html lang="ur" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Geni AI Global Hub - Interactive Gallery</title>
    <style>
        :root {
            --bg-color: #080808;
            --card-bg: #141414;
            --gold-primary: #ffd700;
            --gold-light: #ffea75;
            --text-main: #ffffff;
            --text-muted: #a0a0a0;
            --border-color: #332d00;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            direction: rtl;
            line-height: 1.6;
        }

        header {
            background: linear-gradient(135deg, #111111, #000000);
            border-bottom: 2px solid var(--gold-primary);
            text-align: center;
            padding: 50px 20px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.9);
        }

        header h1 {
            color: var(--gold-primary);
            font-size: 2.8rem;
            margin-bottom: 10px;
            letter-spacing: 1px;
        }

        header p {
            color: var(--text-muted);
            font-size: 1.2rem;
        }

        .container {
            max-width: 1300px;
            margin: 40px auto;
            padding: 0 20px;
        }

        /* گیلری فولڈر ٹیبز (Categories Filters) */
        .filter-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 40px;
        }

        .filter-btn {
            background-color: var(--card-bg);
            color: var(--gold-primary);
            border: 1px solid var(--border-color);
            padding: 12px 24px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .filter-btn:hover, .filter-btn.active {
            background-color: var(--gold-primary);
            color: #000000;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
        }

        /* کارڈز کا گرڈ لے آؤٹ */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 14px;
            overflow: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.6);
        }

        .card:hover {
            transform: translateY(-6px);
            border-color: var(--gold-primary);
            box-shadow: 0 10px 25px rgba(255, 215, 0, 0.2);
        }

        .card img {
            width: 100%;
            height: 350px;
            object-fit: contain;
            background-color: #000;
            padding: 10px;
            border-bottom: 1px solid #222;
        }

        .card-content {
            padding: 20px;
        }

        .card-content h3 {
            color: var(--gold-light);
            font-size: 1.3rem;
            margin-bottom: 8px;
        }

        .card-content p {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        footer {
            text-align: center;
            padding: 30px;
            background-color: #040404;
            color: var(--text-muted);
            border-top: 1px solid #1a1a1a;
            margin-top: 60px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Geni AI Global Hub</h1>
        <p>آفیشل فیچرز گیلری اور اسکرین اسٹوڈیو</p>
    </header>

    <div class="container">
        <!-- فولڈر کیٹیگریز (فلٹر ٹیبز) -->
        <div class="filter-container">
            <button class="filter-btn active" onclick="filterGallery('all')">📂 تمام فولڈرز (All)</button>
            <button class="filter-btn" onclick="filterGallery('ai')">🤖 اے آئی اسٹوڈیو (AI Studio)</button>
            <button class="filter-btn" onclick="filterGallery('wallet')">💰 والٹ اور اسٹور (Wallet & Store)</button>
            <button class="filter-btn" onclick="filterGallery('tools')">🛠️ ٹولز اور ہسٹری (Tools)</button>
            <button class="filter-btn" onclick="filterGallery('profile')">👤 پروفাইল اور سیفٹی (Profile)</button>
        </div>

        <!-- گیلری گرید -->
        <div class="grid" id="galleryGrid">

            <!-- Home -->
            <div class="card" data-category="profile">
                <img src="Images/home.jpg" alt="Home">
                <div class="card-content">
                    <h3>مین ڈیش بورڈ (Home)</h3>
                    <p>مرکزی اسکرین جہاں سے تمام فیچرز اور کوئنز تک رسائی ہوتی ہے۔</p>
                </div>
            </div>

            <!-- Image Generation -->
            <div class="card" data-category="ai">
                <img src="Images/image-generation.jpg" alt="Image Generation">
                <div class="card-content">
                    <h3>اے آئی امیج جنریشن</h3>
                    <p>خوبصورت تصاویر تخلیق کرنے کا طاقتور اسٹوڈیو ماڈیول۔</p>
                </div>
            </div>

            <!-- Image Editor DP -->
            <div class="card" data-category="ai">
                <img src="Images/image-editor-dp.jpg" alt="Image Editor">
                <div class="card-content">
                    <h3>امیج ایڈیٹر اور ڈی پی</h3>
                    <p>تصاویر کو ری سائز اور ایڈٹ کرنے کا انٹرفیس۔</p>
                </div>
            </div>

            <!-- Video AI -->
            <div class="card" data-category="ai">
                <img src="Images/video-ai.jpg" alt="Video AI">
                <div class="card-content">
                    <h3>ویڈیو اے آئی اسٹوڈیو</h3>
                    <p>جدید ویڈیو جنریشن اور ایڈیٹنگ کی اسکرین۔</p>
                </div>
            </div>

            <!-- Voice AI -->
            <div class="card" data-category="ai">
                <img src="Images/voice-ai.jpg" alt="Voice AI">
                <div class="card-content">
                    <h3>وائس اے آئی ماڈیول</h3>
                    <p>آواز اور صوتی خصوصیات کا شاندار انٹرفیس۔</p>
                </div>
            </div>

            <!-- Wallet Rewards Menu -->
            <div class="card" data-category="wallet">
                <img src="Images/wallet-rewards-menu.jpg" alt="Wallet">
                <div class="card-content">
                    <h3>والٹ اور ریوارڈز مینو</h3>
                    <p>کوئنز بیلنس، ڈیلی چیک ان اور ریفرل سسٹم کا مرکز۔</p>
                </div>
            </div>

            <!-- Watch Ad Reward -->
            <div class="card" data-category="wallet">
                <img src="Images/watch-ad-reward.jpg" alt="Ad Reward">
                <div class="card-content">
                    <h3>ایڈ ریوارڈ سسٹم</h3>
                    <p>اشتہار دیکھ کر مفت کریڈٹس اور پوائنٹس حاصل کرنے کی اسکرین۔</p>
                </div>
            </div>

            <!-- Store -->
            <div class="card" data-category="wallet">
                <img src="Images/store.jpg" alt="Store">
                <div class="card-content">
                    <h3>کریڈٹ اسٹور 1</h3>
                    <p>گولڈ اور سلور پیکیجز کی خریداری کا آفیشل اسٹور۔</p>
                </div>
            </div>

            <!-- Store 1 -->
            <div class="card" data-category="wallet">
                <img src="Images/store 1.jpg" alt="Store 1">
                <div class="card-content">
                    <h3>کریڈٹ اسٹور 2</h3>
                    <p>مزید پیکیجز اور آفرز کی تفصیلات پر مشتمل اسکرین۔</p>
                </div>
            </div>

            <!-- Invite -->
            <div class="card" data-category="wallet">
                <img src="Images/invite.jpg" alt="Invite">
                <div class="card-content">
                    <h3>ریفرل انوائٹ سسٹم</h3>
                    <p>دوستوں کو دعوت دے کر اضافی کوئنز کمانے کا صفحہ۔</p>
                </div>
            </div>

            <!-- Audio Tools -->
            <div class="card" data-category="tools">
                <img src="Images/audio-tools.jpg" alt="Audio Tools">
                <div class="card-content">
                    <h3>آڈیو ٹولز</h3>
                    <p>آڈیو ریکارڈنگ اور پلے بیک کی سہولیات۔</p>
                </div>
            </div>

            <!-- Voice Library -->
            <div class="card" data-category="tools">
                <img src="Images/voice-library.jpg" alt="Voice Library">
                <div class="card-content">
                    <h3>وائس لائبریری</h3>
                    <p>محفوظ شدہ آوازوں اور کلپس کا ذخیرہ۔</p>
                </div>
            </div>

            <!-- History -->
            <div class="card" data-category="tools">
                <img src="Images/history.jpg" alt="History">
                <div class="card-content">
                    <h3>جنرل ہسٹری</h3>
                    <p>آپ کے پچھلے تمام سیشنز اور سرگرمیوں کا ریکارڈ۔</p>
                </div>
            </div>

            <!-- Image History -->
            <div class="card" data-category="tools">
                <img src="Images/image-history.jpg" alt="Image History">
                <div class="card-content">
                    <h3>امیج ہسٹری</h3>
                    <p>پہلے سے بنائی گئی تمام تصاویر کا ریکارڈ۔</p>
                </div>
            </div>

            <!-- Video History -->
            <div class="card" data-category="tools">
                <img src="Images/video-history.jpg" alt="Video History">
                <div class="card-content">
                    <h3>ویڈیو ہسٹری</h3>
                    <p>تخلیق کردہ ویڈیوز کی ہسٹری اسکرین۔</p>
                </div>
            </div>

            <!-- Voice History -->
            <div class="card" data-category="tools">
                <img src="Images/voice-history.jpg" alt="Voice History">
                <div class="card-content">
                    <h3>وائس ہسٹری</h3>
                    <p>پچھلی وائس جنریشنز کی تفصیلات۔</p>
                </div>
            </div>

            <!-- Profile -->
            <div class="card" data-category="profile">
                <img src="Images/profile.jpg" alt="Profile">
                <div class="card-content">
                    <h3>یوزر پروفাইল</h3>
                    <p>اکاؤنٹ کی بنیادی معلومات اور ترتیبات۔</p>
                </div>
            </div>

            <!-- Account Safety -->
            <div class="card" data-category="profile">
                <img src="Images/account-safety.jpg" alt="Safety">
                <div class="card-content">
                    <h3>اکاؤنٹ سیکیورٹی</h3>
                    <p>حفاظتی ضوابط اور اکاؤنٹ پروٹیکشن مینو۔</p>
                </div>
            </div>

            <!-- AI Error -->
            <div class="card" data-category="profile">
                <img src="Images/ai-error.jpg" alt="Error Handling">
                <div class="card-content">
                    <h3>سسٹم نوٹیفیکیشن / الرٹ</h3>
                    <p>نیٹ ورک یا سرور ایرر کی صورت میں گائیڈنس اسکرین۔</p>
                </div>
            </div>

        </div>
    </div>

    <footer>
        <p>&copy; 2026 Geni AI Global Hub. تمام حقوق محفوظ ہیں۔</p>
    </footer>

    <script>
        function filterGallery(category) {
            // بٹن کی ایکٹیو کلاس تبدیل کرنا
            const buttons = document.querySelectorAll('.filter-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

            // کارڈز کو فلٹر کرنا
            const cards = document.querySelectorAll('.card');
            cards.forEach(card => {
                if (category === 'all' || card.getAttribute('data-category') === category) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        }
    </script>

</body>
</html>