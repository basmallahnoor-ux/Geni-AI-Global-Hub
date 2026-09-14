<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Geni AI Global Hub - Official Gallery</title>
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
        <p>Official Mobile App Features & Screens Gallery</p>
    </header>

    <div class="container">
        <!-- Categories Filter -->
        <div class="filter-container">
            <button class="filter-btn active" onclick="filterGallery('all')">📂 All Folders</button>
            <button class="filter-btn" onclick="filterGallery('ai')">🤖 AI Studio</button>
            <button class="filter-btn" onclick="filterGallery('wallet')">💰 Wallet & Store</button>
            <button class="filter-btn" onclick="filterGallery('tools')">🛠️ Tools & History</button>
            <button class="filter-btn" onclick="filterGallery('profile')">👤 Profile & Safety</button>
        </div>

        <!-- Gallery Grid -->
        <div class="grid" id="galleryGrid">

            <div class="card" data-category="profile">
                <img src="images/home.jpg" alt="Home">
                <div class="card-content">
                    <h3>Main Dashboard</h3>
                    <p>Central screen showing AI features and live coin balances simultaneously.</p>
                </div>
            </div>

            <div class="card" data-category="ai">
                <img src="images/image-generation.jpg" alt="Image Generation">
                <div class="card-content">
                    <h3>AI Image Generation</h3>
                    <p>Powerful studio module designed for generating stunning and creative images.</p>
                </div>
            </div>

            <div class="card" data-category="ai">
                <img src="images/image-editor-dp.jpg" alt="Image Editor">
                <div class="card-content">
                    <h3>Image Editor & DP</h3>
                    <p>Interface for editing, resizing, and tailoring pictures for profile displays.</p>
                </div>
            </div>

            <div class="card" data-category="ai">
                <img src="images/video-ai.jpg" alt="Video AI">
                <div class="card-content">
                    <h3>Video AI Studio</h3>
                    <p>Advanced cutting-edge module to generate and manage AI videos seamlessly.</p>
                </div>
            </div>

            <div class="card" data-category="ai">
                <img src="images/voice-ai.jpg" alt="Voice AI">
                <div class="card-content">
                    <h3>Voice AI Module</h3>
                    <p>Stunning interface for voice cloning, synthesis, and audio processing.</p>
                </div>
            </div>

            <div class="card" data-category="wallet">
                <img src="images/wallet-rewards-menu.jpg" alt="Wallet">
                <div class="card-content">
                    <h3>Wallet & Rewards Menu</h3>
                    <p>Complete financial hub managing coin balance, daily check-ins, and referrals.</p>
                </div>
            </div>

            <div class="card" data-category="wallet">
                <img src="images/watch-ad-reward.jpg" alt="Ad Reward">
                <div class="card-content">
                    <h3>Ad Reward System</h3>
                    <p>Earn free currency instantly by watching rewarded video advertisements.</p>
                </div>
            </div>

            <div class="card" data-category="wallet">
                <img src="images/store.jpg" alt="Store">
                <div class="card-content">
                    <h3>Credit Store (Package 1)</h3>
                    <p>Store interface to purchase affordable gold and silver coin packages.</p>
                </div>
            </div>

            <div class="card" data-category="wallet">
                <img src="images/store 1.jpg" alt="Store 1">
                <div class="card-content">
                    <h3>Credit Store (Package 2)</h3>
                    <p>Detailed listing of additional credit offers and bundle pricing.</p>
                </div>
            </div>

            <div class="card" data-category="wallet">
                <img src="images/invite.jpg" alt="Invite">
                <div class="card-content">
                    <h3>Referral Invite System</h3>
                    <p>Invite friends via QR code sharing to earn bonus coins together.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/audio-tools.jpg" alt="Audio Tools">
                <div class="card-content">
                    <h3>Audio Tools</h3>
                    <p>Modern utilities supporting microphone recording and high-quality audio playback.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/voice-library.jpg" alt="Voice Library">
                <div class="card-content">
                    <h3>Voice Library</h3>
                    <p>Organized repository storing saved voice clips, audio samples, and outputs.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/history.jpg" alt="History">
                <div class="card-content">
                    <h3>General History</h3>
                    <p>Comprehensive activity log tracking all previous user sessions and events.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/image-history.jpg" alt="Image History">
                <div class="card-content">
                    <h3>Image History</h3>
                    <p>Dedicated gallery archiving previously generated images and artwork.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/video-history.jpg" alt="Video History">
                <div class="card-content">
                    <h3>Video History</h3>
                    <p>Playback panel and record log of all previously created AI videos.</p>
                </div>
            </div>

            <div class="card" data-category="tools">
                <img src="images/voice-history.jpg" alt="Voice History">
                <div class="card-content">
                    <h3>Voice History</h3>
                    <p>Detailed breakdown and logs of previous voice generations and tasks.</p>
                </div>
            </div>

            <div class="card" data-category="profile">
                <img src="images/profile.jpg" alt="Profile">
                <div class="card-content">
                    <h3>User Profile</h3>
                    <p>Account settings, user identification, and personal preference controls.</p>
                </div>
            </div>

            <div class="card" data-category="profile">
                <img src="images/account-safety.jpg" alt="Safety">
                <div class="card-content">
                    <h3>Account Safety</h3>
                    <p>Security guidelines, policy warnings, and account protection hub.</p>
                </div>
            </div>

            <div class="card" data-category="profile">
                <img src="images/ai-error.jpg" alt="Error Handling">
                <div class="card-content">
                    <h3>System Alert / Notice</h3>
                    <p>Guidance screen helping users handle network connection or server errors.</p>
                </div>
            </div>

        </div>
    </div>

    <footer>
        <p>&copy; 2026 Geni AI Global Hub. All rights reserved.</p>
    </footer>

    <script>
        function filterGallery(category) {
            const buttons = document.querySelectorAll('.filter-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

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
