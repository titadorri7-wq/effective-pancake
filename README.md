<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مجموعه موزیک من</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://accounts.google.com/gsi/client" async defer></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Vazirmatn', sans-serif;
        }
        
        .music-card {
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
        
        .music-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }
        
        .play-btn {
            transition: all 0.3s ease;
        }
        
        .play-btn:hover {
            transform: scale(1.1);
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .qr-code {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        
        .admin-panel {
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
        }
        
        .rating-stars {
            display: flex;
            gap: 2px;
            justify-content: center;
            margin-top: 10px;
        }
        
        .star {
            cursor: pointer;
            font-size: 18px;
            transition: all 0.2s ease;
        }
        
        .star:hover {
            transform: scale(1.2);
        }
        
        .star.active {
            color: #fbbf24;
        }
        
        .star.inactive {
            color: #d1d5db;
        }
    </style>
</head>
<body class="gradient-bg min-h-screen">
    <!-- Login Modal -->
    <div id="loginModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="admin-panel rounded-2xl p-8 max-w-md w-full mx-4 text-center">
            <h2 class="text-3xl font-bold text-gray-800 mb-6">🎵 ورود به سایت موزیک</h2>
            <p class="text-gray-600 mb-6">برای دسترسی به سایت، لطفاً وارد شوید</p>
            <div id="g_id_onload"
                 data-client_id="YOUR_GOOGLE_CLIENT_ID"
                 data-callback="handleCredentialResponse">
            </div>
            <div class="g_id_signin" data-type="standard" data-size="large" data-theme="outline" data-text="sign_in_with" data-shape="rectangular" data-logo_alignment="left"></div>
            
            <!-- Demo Login Button -->
            <div class="mt-4 pt-4 border-t border-gray-300">
                <p class="text-sm text-gray-500 mb-3">برای تست (بدون Gmail واقعی):</p>
                <button onclick="demoLogin()" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition-colors font-medium">
                    ورود آزمایشی
                </button>
            </div>
        </div>
    </div>

    <!-- Header -->
    <header class="text-white py-8 text-center">
        <div class="flex justify-between items-center max-w-6xl mx-auto px-6">
            <div id="userInfo" class="hidden text-right">
                <p class="text-sm opacity-80">خوش آمدید</p>
                <p class="font-medium" id="userName"></p>
            </div>
            <div class="flex-1">
                <h1 class="text-4xl font-bold mb-2">🎵 مجموعه موزیک من</h1>
                <p class="text-lg opacity-90">بهترین آهنگ‌های من را اینجا پیدا کنید</p>
            </div>
            <button id="logoutBtn" onclick="logout()" class="hidden bg-red-500 bg-opacity-20 text-white px-4 py-2 rounded-lg hover:bg-opacity-30 transition-colors">
                خروج
            </button>
        </div>
        
        <!-- QR Code Section -->
        <div class="mt-8 flex justify-center">
            <div class="qr-code">
                <div class="text-center mb-3">
                    <p class="text-gray-700 font-medium">برای دسترسی سریع اسکن کنید</p>
                </div>
                <div id="qrcode" class="flex justify-center">
                    <!-- QR Code SVG -->
                    <svg width="120" height="120" viewBox="0 0 120 120" class="border-2 border-gray-300 rounded-lg">
                        <rect width="120" height="120" fill="white"/>
                        <rect x="10" y="10" width="30" height="30" fill="black"/>
                        <rect x="80" y="10" width="30" height="30" fill="black"/>
                        <rect x="10" y="80" width="30" height="30" fill="black"/>
                        <rect x="15" y="15" width="20" height="20" fill="white"/>
                        <rect x="85" y="15" width="20" height="20" fill="white"/>
                        <rect x="15" y="85" width="20" height="20" fill="white"/>
                        <rect x="20" y="20" width="10" height="10" fill="black"/>
                        <rect x="90" y="20" width="10" height="10" fill="black"/>
                        <rect x="20" y="90" width="10" height="10" fill="black"/>
                        <rect x="50" y="15" width="5" height="5" fill="black"/>
                        <rect x="60" y="15" width="5" height="5" fill="black"/>
                        <rect x="50" y="25" width="5" height="5" fill="black"/>
                        <rect x="70" y="25" width="5" height="5" fill="black"/>
                        <rect x="45" y="35" width="5" height="5" fill="black"/>
                        <rect x="55" y="35" width="5" height="5" fill="black"/>
                        <rect x="65" y="35" width="5" height="5" fill="black"/>
                        <rect x="75" y="35" width="5" height="5" fill="black"/>
                        <rect x="15" y="50" width="5" height="5" fill="black"/>
                        <rect x="25" y="50" width="5" height="5" fill="black"/>
                        <rect x="35" y="50" width="5" height="5" fill="black"/>
                        <rect x="50" y="50" width="5" height="5" fill="black"/>
                        <rect x="60" y="50" width="5" height="5" fill="black"/>
                        <rect x="70" y="50" width="5" height="5" fill="black"/>
                        <rect x="85" y="50" width="5" height="5" fill="black"/>
                        <rect x="95" y="50" width="5" height="5" fill="black"/>
                        <rect x="105" y="50" width="5" height="5" fill="black"/>
                        <rect x="45" y="60" width="5" height="5" fill="black"/>
                        <rect x="65" y="60" width="5" height="5" fill="black"/>
                        <rect x="75" y="60" width="5" height="5" fill="black"/>
                        <rect x="50" y="70" width="5" height="5" fill="black"/>
                        <rect x="60" y="70" width="5" height="5" fill="black"/>
                        <rect x="80" y="70" width="5" height="5" fill="black"/>
                        <rect x="90" y="70" width="5" height="5" fill="black"/>
                        <rect x="100" y="70" width="5" height="5" fill="black"/>
                    </svg>
                </div>
            </div>
        </div>
    </header>

    <!-- Admin Panel -->
    <div id="adminPanel" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="admin-panel rounded-2xl p-8 max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 text-center">افزودن آهنگ جدید</h3>
            <div class="space-y-4">
                <input type="text" id="songTitle" placeholder="نام آهنگ" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                <input type="text" id="artistName" placeholder="نام خواننده" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                <input type="text" id="albumName" placeholder="نام آلبوم" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                <input type="file" id="musicFile" accept="audio/*" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                <p class="text-sm text-gray-600">فایل موزیک خود را انتخاب کنید (MP3, WAV, OGG)</p>
                <div class="flex gap-3">
                    <button onclick="addSong()" class="flex-1 bg-green-500 text-white py-3 rounded-lg hover:bg-green-600 transition-colors font-medium">افزودن</button>
                    <button onclick="closeAdmin()" class="flex-1 bg-gray-500 text-white py-3 rounded-lg hover:bg-gray-600 transition-colors font-medium">لغو</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Music Collection -->
    <main class="container mx-auto px-6 pb-12">
        <div id="musicGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- Songs will be rendered here -->
        </div>
    </main>

    <!-- Admin Access Button (Only for admin) -->
    <div id="adminBtn" class="hidden fixed bottom-4 left-4">
        <button onclick="openAdmin()" class="bg-green-600 bg-opacity-80 text-white p-4 rounded-full hover:bg-opacity-100 transition-all shadow-lg">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
            </svg>
        </button>
    </div>

    <script>
        // Admin email - اینجا ایمیل خودتان را وارد کنید
        const ADMIN_EMAIL = "your-email@gmail.com"; // ایمیل خودتان را اینجا بنویسید
        
        let currentUser = null;
        let isAdmin = false;
        let musicCollection = [];
        let currentlyPlaying = null;

        // Color and icon options
        const colorOptions = [
            "from-pink-400 to-purple-600",
            "from-blue-400 to-indigo-600", 
            "from-green-400 to-teal-600",
            "from-yellow-400 to-orange-600",
            "from-red-400 to-pink-600",
            "from-indigo-400 to-purple-600"
        ];

        const iconOptions = ["🎵", "🎶", "🎼", "🎤", "🎧", "🎸", "🎹", "🥁"];

        // Google Sign-In callback
        function handleCredentialResponse(response) {
            const responsePayload = decodeJwtResponse(response.credential);
            
            currentUser = {
                email: responsePayload.email,
                name: responsePayload.name,
                picture: responsePayload.picture
            };

            // Check if user is admin
            isAdmin = currentUser.email === ADMIN_EMAIL;
            
            loginSuccess();
        }

        // Demo login function
        function demoLogin() {
            currentUser = {
                email: "demo@example.com",
                name: "کاربر آزمایشی",
                picture: null
            };
            isAdmin = true; // For demo purposes
            loginSuccess();
        }

        function loginSuccess() {
            document.getElementById('loginModal').classList.add('hidden');
            document.getElementById('userInfo').classList.remove('hidden');
            document.getElementById('logoutBtn').classList.remove('hidden');
            document.getElementById('userName').textContent = currentUser.name;
            
            if (isAdmin) {
                document.getElementById('adminBtn').classList.remove('hidden');
            }
            
            loadMusicCollection();
            renderMusicGrid();
        }

        function logout() {
            currentUser = null;
            isAdmin = false;
            document.getElementById('loginModal').classList.remove('hidden');
            document.getElementById('userInfo').classList.add('hidden');
            document.getElementById('logoutBtn').classList.add('hidden');
            document.getElementById('adminBtn').classList.add('hidden');
            
            // Clear music collection for security
            musicCollection = [];
            renderMusicGrid();
        }

        function decodeJwtResponse(token) {
            const base64Url = token.split('.')[1];
            const base64 = base64Url.replace(/-/g, '+').replace(/_/g, '/');
            const jsonPayload = decodeURIComponent(atob(base64).split('').map(function(c) {
                return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
            }).join(''));
            return JSON.parse(jsonPayload);
        }

        function openAdmin() {
            if (!isAdmin) {
                alert("شما مجاز به دسترسی به این بخش نیستید!");
                return;
            }
            document.getElementById('adminPanel').classList.remove('hidden');
        }

        function closeAdmin() {
            document.getElementById('adminPanel').classList.add('hidden');
            document.getElementById('songTitle').value = '';
            document.getElementById('artistName').value = '';
            document.getElementById('albumName').value = '';
            document.getElementById('musicFile').value = '';
        }

        function addSong() {
            if (!isAdmin) {
                alert("فقط مدیر می‌تواند آهنگ اضافه کند!");
                return;
            }

            const title = document.getElementById('songTitle').value.trim();
            const artist = document.getElementById('artistName').value.trim();
            const album = document.getElementById('albumName').value.trim();
            const fileInput = document.getElementById('musicFile');

            if (!title || !artist || !album) {
                alert("لطفاً تمام فیلدها را پر کنید!");
                return;
            }

            if (!fileInput.files[0]) {
                alert("لطفاً فایل موزیک را انتخاب کنید!");
                return;
            }

            const file = fileInput.files[0];
            
            if (!file.type.startsWith('audio/')) {
                alert("لطفاً فقط فایل صوتی انتخاب کنید!");
                return;
            }

            const audioURL = URL.createObjectURL(file);
            const randomColor = colorOptions[Math.floor(Math.random() * colorOptions.length)];
            const randomIcon = iconOptions[Math.floor(Math.random() * iconOptions.length)];
            
            const newSong = {
                id: Date.now(),
                title: title,
                artist: artist,
                album: album,
                color: randomColor,
                icon: randomIcon,
                audioURL: audioURL,
                fileName: file.name,
                ratings: [],
                averageRating: 0
            };

            musicCollection.push(newSong);
            saveMusicCollection();
            renderMusicGrid();
            closeAdmin();
            alert("آهنگ با موفقیت اضافه شد!");
        }

        function rateSong(songId, rating) {
            const song = musicCollection.find(s => s.id === songId);
            if (!song) return;

            // Remove previous rating from this user if exists
            song.ratings = song.ratings.filter(r => r.user !== currentUser.email);
            
            // Add new rating
            song.ratings.push({
                user: currentUser.email,
                rating: rating,
                date: new Date().toISOString()
            });

            // Calculate average
            song.averageRating = song.ratings.reduce((sum, r) => sum + r.rating, 0) / song.ratings.length;
            
            saveMusicCollection();
            renderMusicGrid();
        }

        function renderMusicGrid() {
            const grid = document.getElementById('musicGrid');
            grid.innerHTML = '';

            if (musicCollection.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full text-center text-white py-12">
                        <div class="text-6xl mb-4">🎵</div>
                        <h3 class="text-2xl font-bold mb-2">هنوز آهنگی اضافه نشده</h3>
                        <p class="opacity-80">${isAdmin ? 'برای اضافه کردن آهنگ، روی دکمه ستاره کلیک کنید' : 'به زودی آهنگ‌های جدید اضافه خواهد شد'}</p>
                    </div>
                `;
                return;
            }

            musicCollection.forEach((song, index) => {
                const userRating = song.ratings.find(r => r.user === currentUser.email);
                const songCard = document.createElement('div');
                songCard.className = 'music-card bg-white bg-opacity-20 rounded-2xl p-6 text-white';
                songCard.innerHTML = `
                    <div class="flex items-center justify-between mb-4">
                        <div class="w-16 h-16 bg-gradient-to-br ${song.color} rounded-xl flex items-center justify-center text-2xl">${song.icon}</div>
                        <button class="play-btn bg-white bg-opacity-20 hover:bg-opacity-30 rounded-full p-3" onclick="togglePlay(${index})">
                            <svg class="play-icon" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M8 5v14l11-7z"/>
                            </svg>
                            <svg class="pause-icon hidden" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"/>
                            </svg>
                        </button>
                    </div>
                    <h3 class="text-xl font-bold mb-2">${song.title}</h3>
                    <p class="text-sm opacity-80 mb-1">${song.artist}</p>
                    <p class="text-xs opacity-60 mb-3">${song.album}</p>
                    
                    <!-- Rating Section -->
                    <div class="border-t border-white border-opacity-20 pt-3">
                        <div class="flex items-center justify-between mb-2">
                            <span class="text-xs opacity-70">امتیاز:</span>
                            <span class="text-sm font-medium">${song.averageRating ? song.averageRating.toFixed(1) : '0'} ⭐ (${song.ratings.length})</span>
                        </div>
                        <div class="rating-stars">
                            ${[1,2,3,4,5].map(star => `
                                <span class="star ${userRating && userRating.rating >= star ? 'active' : 'inactive'}" 
                                      onclick="rateSong(${song.id}, ${star})">⭐</span>
                            `).join('')}
                        </div>
                        ${userRating ? `<p class="text-xs opacity-60 text-center mt-1">شما: ${userRating.rating} ستاره</p>` : ''}
                    </div>
                    
                    <audio class="hidden" preload="metadata" src="${song.audioURL}"></audio>
                `;
                grid.appendChild(songCard);
            });
        }

        function togglePlay(songIndex) {
            const songCards = document.querySelectorAll('.music-card');
            const currentCard = songCards[songIndex];
            const audio = currentCard.querySelector('audio');
            const playBtn = currentCard.querySelector('.play-btn');
            const playIcon = playBtn.querySelector('.play-icon');
            const pauseIcon = playBtn.querySelector('.pause-icon');

            if (currentlyPlaying !== null && currentlyPlaying !== songIndex) {
                const prevCard = songCards[currentlyPlaying];
                const prevAudio = prevCard.querySelector('audio');
                const prevPlayBtn = prevCard.querySelector('.play-btn');
                const prevPlayIcon = prevPlayBtn.querySelector('.play-icon');
                const prevPauseIcon = prevPlayBtn.querySelector('.pause-icon');
                
                prevAudio.pause();
                prevPlayIcon.classList.remove('hidden');
                prevPauseIcon.classList.add('hidden');
            }

            if (audio.paused) {
                audio.play().then(() => {
                    playIcon.classList.add('hidden');
                    pauseIcon.classList.remove('hidden');
                    currentlyPlaying = songIndex;
                }).catch(error => {
                    console.error('Error playing audio:', error);
                    alert('خطا در پخش فایل صوتی.');
                });
            } else {
                audio.pause();
                playIcon.classList.remove('hidden');
                pauseIcon.classList.add('hidden');
                currentlyPlaying = null;
            }

            audio.onended = function() {
                playIcon.classList.remove('hidden');
                pauseIcon.classList.add('hidden');
                currentlyPlaying = null;
            };
        }

        function saveMusicCollection() {
            localStorage.setItem('musicCollection', JSON.stringify(musicCollection));
        }

        function loadMusicCollection() {
            const saved = localStorage.getItem('musicCollection');
            if (saved) {
                musicCollection = JSON.parse(saved);
            }
        }

        // Initialize page
        window.onload = function() {
            // Show login modal on page load
            document.getElementById('loginModal').classList.remove('hidden');
        };
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'974181dbd5500618',t:'MTc1NjAyNDQzMi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

