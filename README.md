# s1vagemamba.github.Io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>One Ummah - United Social Media</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#006D5B',
                        secondary: '#FFC857',
                        accent: '#E63946',
                        dark: {
                            bg: '#0F172A',
                            card: '#1E293B',
                            text: '#E2E8F0'
                        },
                        light: {
                            bg: '#F8FAFC',
                            card: '#FFFFFF',
                            text: '#1E293B'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        .post-image {
            aspect-ratio: 4 / 5;
            object-fit: cover;
        }
        
        .story-ring {
            background: conic-gradient(#006D5B 0%, #FFC857 50%, #006D5B 100%);
        }

        /* Smooth transitions */
        .transition-all {
            transition: all 0.3s ease;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(0, 109, 91, 0.5);
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: rgba(0, 109, 91, 0.8);
        }
    </style>
    <script>
        // Toggle Dark Mode
        document.addEventListener('DOMContentLoaded', () => {
            const darkModeToggle = document.getElementById('dark-mode-toggle');
            const html = document.documentElement;

            darkModeToggle.addEventListener('click', () => {
                if (html.classList.contains('dark')) {
                    html.classList.remove('dark');
                    localStorage.setItem('theme', 'light');
                } else {
                    html.classList.add('dark');
                    localStorage.setItem('theme', 'dark');
                }
            });

            // Load theme from local storage
            if (localStorage.getItem('theme') === 'dark') {
                html.classList.add('dark');
            }
        });
    </script>
</head>
<body class="bg-light-bg dark:bg-dark-bg text-light-text dark:text-dark-text transition-all min-h-screen">
    <div id="app" class="flex flex-col min-h-screen">
        <!-- Navigation -->
        <nav class="sticky top-0 bg-white dark:bg-dark-card shadow-sm z-50 transition-all">
            <div class="max-w-screen-xl mx-auto px-4">
                <div class="flex items-center justify-between h-16">
                    <div class="flex items-center space-x-4">
                        <div class="flex items-center">
                            <svg class="w-8 h-8 text-primary" viewBox="0 0 24 24" fill="currentColor">
                                <path d="M12,2C6.486,2,2,6.486,2,12s4.486,10,10,10s10-4.486,10-10S17.514,2,12,2z M12,20c-4.411,0-8-3.589-8-8 s3.589-8,8-8s8,3.589,8,8S16.411,20,12,20z"/>
                                <path d="M12,4c-1.654,0-3,1.346-3,3s1.346,3,3,3s3-1.346,3-3S13.654,4,12,4z"/>
                                <path d="M12,14c-3.309,0-6,1.691-6,5h12C18,15.691,15.309,14,12,14z"/>
                            </svg>
                            <h1 class="text-xl font-bold text-primary ml-2">One Ummah</h1>
                        </div>
                        <div class="relative hidden md:block">
                            <input type="text" placeholder="Search" class="bg-gray-100 dark:bg-dark-bg rounded-full py-2 pl-10 pr-4 w-64 text-base focus:outline-none focus:ring-2 focus:ring-primary">
                            <i class="fas fa-search absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400"></i>
                        </div>
                    </div>
                    <div class="flex items-center space-x-4">
                        <button id="notifications-btn" class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-all relative">
                            <i class="fas fa-bell"></i>
                            <span class="absolute top-0 right-0 w-3 h-3 bg-accent rounded-full border border-white dark:border-dark-card"></span>
                        </button>
                        <button id="create-post-btn" class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-all">
                            <i class="fas fa-plus"></i>
                        </button>
                        <button id="dark-mode-toggle" class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-all">
                            <i class="fas fa-moon dark:hidden"></i>
                            <i class="fas fa-sun hidden dark:block"></i>
                        </button>
                        <button id="profile-btn" class="w-8 h-8 rounded-full bg-primary text-white flex items-center justify-center">
                            <span>U</span>
                        </button>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Tabs -->
        <div class="bg-white dark:bg-dark-card sticky top-16 shadow-sm z-40 transition-all">
            <div class="max-w-screen-xl mx-auto">
                <div class="flex justify-around">
                    <button class="tab-btn py-4 px-6 border-b-2 border-primary font-medium text-primary" data-tab="feed">
                        <i class="fas fa-home"></i> <span class="hidden sm:inline ml-1">Feed</span>
                    </button>
                    <button class="tab-btn py-4 px-6 border-b-2 border-transparent font-medium text-gray-500 dark:text-gray-400" data-tab="explore">
                        <i class="fas fa-compass"></i> <span class="hidden sm:inline ml-1">Explore</span>
                    </button>
                    <button class="tab-btn py-4 px-6 border-b-2 border-transparent font-medium text-gray-500 dark:text-gray-400" data-tab="communities">
                        <i class="fas fa-users"></i> <span class="hidden sm:inline ml-1">Communities</span>
                    </button>
                    <button class="tab-btn py-4 px-6 border-b-2 border-transparent font-medium text-gray-500 dark:text-gray-400" data-tab="messages">
                        <i class="fas fa-comment"></i> <span class="hidden sm:inline ml-1">Messages</span>
                    </button>
                    <button class="tab-btn py-4 px-6 border-b-2 border-transparent font-medium text-gray-500 dark:text-gray-400" data-tab="learn">
                        <i class="fas fa-graduation-cap"></i> <span class="hidden sm:inline ml-1">Learn</span>
                    </button>
                </div>
            </div>
        </div>

        <!-- Main Content -->
        <main class="flex-grow max-w-screen-xl mx-auto w-full px-4 py-6">
            <div id="feed-tab" class="tab-content">
                <h1 class="text-2xl font-bold">Welcome to One Ummah!</h1>
                <p>This is your social media feed.</p>
            </div>
        </main>
    </div>
</body>
</html>
