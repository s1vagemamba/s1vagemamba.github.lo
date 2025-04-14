<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        .story-ring {
            padding: 2px;
            background: conic-gradient(#006D5B 0%, #FFC857 50%, #006D5B 100%);
            border-radius: 50%;
        }
        
        .create-post-modal {
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(5px);
        }
        
        .comment-input:focus {
            box-shadow: none !important;
        }
    </style>
</head>
<body class="bg-light-bg dark:bg-dark-bg text-light-text dark:text-dark-text transition-all min-h-screen">
    <div id="app" class="flex flex-col min-h-screen">
        <!-- Navigation remains the same -->

        <!-- Stories Section -->
        <div class="bg-white dark:bg-dark-card py-4 border-b overflow-x-auto">
            <div class="max-w-screen-xl mx-auto px-4 flex space-x-4">
                <!-- Story Items -->
                <div class="flex flex-col items-center space-y-1">
                    <div class="story-ring w-16 h-16 flex items-center justify-center">
                        <div class="bg-white dark:bg-dark-card rounded-full p-1">
                            <img src="https://via.placeholder.com/56" class="w-14 h-14 rounded-full object-cover">
                        </div>
                    </div>
                    <span class="text-xs">Your Story</span>
                </div>
                <!-- Add more story items here -->
            </div>
        </div>

        <!-- Main Content -->
        <main class="flex-grow max-w-screen-xl mx-auto w-full px-4 py-6">
            <!-- Create Post Card -->
            <div class="bg-white dark:bg-dark-card rounded-lg shadow mb-6 p-4">
                <div class="flex items-center space-x-4">
                    <img src="https://via.placeholder.com/48" class="w-12 h-12 rounded-full">
                    <button id="create-post-btn" class="flex-grow bg-gray-100 dark:bg-dark-bg text-left px-4 py-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700 transition-all">
                        What's on your mind?
                    </button>
                </div>
            </div>

            <!-- Feed Posts -->
            <div class="space-y-6">
                <!-- Sample Post -->
                <div class="bg-white dark:bg-dark-card rounded-lg shadow">
                    <div class="p-4">
                        <div class="flex items-center justify-between">
                            <div class="flex items-center space-x-3">
                                <img src="https://via.placeholder.com/40" class="w-10 h-10 rounded-full">
                                <div>
                                    <h3 class="font-semibold">User Name</h3>
                                    <p class="text-sm text-gray-500">2 hours ago</p>
                                </div>
                            </div>
                            <button class="text-gray-500 hover:text-gray-700 dark:hover:text-gray-300">
                                <i class="fas fa-ellipsis-h"></i>
                            </button>
                        </div>
                        <p class="mt-4">This is a sample post content. Let's build a strong community together! 🤝</p>
                        <img src="https://via.placeholder.com/600x400" class="mt-4 rounded-lg w-full object-cover">
                    </div>
                    <div class="border-t dark:border-gray-700 px-4 py-2">
                        <div class="flex items-center space-x-4 text-gray-500">
                            <button class="flex items-center space-x-1 hover:text-primary">
                                <i class="far fa-heart"></i>
                                <span>1.2K</span>
                            </button>
                            <button class="flex items-center space-x-1 hover:text-primary">
                                <i class="far fa-comment"></i>
                                <span>284</span>
                            </button>
                            <button class="flex items-center space-x-1 hover:text-primary">
                                <i class="far fa-share-square"></i>
                                <span>Share</span>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <!-- Create Post Modal -->
        <div id="create-post-modal" class="fixed inset-0 z-50 create-post-modal hidden">
            <div class="flex items-center justify-center min-h-screen">
                <div class="bg-white dark:bg-dark-card rounded-lg w-full max-w-2xl mx-4 p-6">
                    <div class="flex justify-between items-center mb-4">
                        <h2 class="text-xl font-bold">Create Post</h2>
                        <button id="close-modal-btn" class="text-gray-500 hover:text-gray-700 dark:hover:text-gray-300">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    <textarea class="w-full bg-transparent focus:outline-none resize-none mb-4" 
                              placeholder="Write your post here..." 
                              rows="4"></textarea>
                    <div class="flex justify-between items-center">
                        <div class="flex space-x-2">
                            <button class="p-2 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-full">
                                <i class="fas fa-image text-primary"></i>
                            </button>
                            <button class="p-2 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-full">
                                <i class="fas fa-video text-secondary"></i>
                            </button>
                        </div>
                        <button class="bg-primary text-white px-6 py-2 rounded-full hover:bg-opacity-90">
                            Post
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Add this script at the end of body -->
    <script>
        // Modal Handling
        const createPostBtn = document.getElementById('create-post-btn');
        const closeModalBtn = document.getElementById('close-modal-btn');
        const modal = document.getElementById('create-post-modal');

        createPostBtn.addEventListener('click', () => modal.classList.remove('hidden'));
        closeModalBtn.addEventListener('click', () => modal.classList.add('hidden'));

        // Tab Switching
        document.querySelectorAll('.tab-btn').forEach(button => {
            button.addEventListener('click', () => {
                // Remove active classes
                document.querySelectorAll('.tab-btn').forEach(btn => {
                    btn.classList.remove('border-primary', 'text-primary');
                    btn.classList.add('border-transparent', 'text-gray-500');
                });

                // Add active class to clicked button
                button.classList.add('border-primary', 'text-primary');
                button.classList.remove('border-transparent', 'text-gray-500');

                // Hide all tab contents
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.classList.add('hidden');
                });

                // Show selected tab content
                const tabId = button.dataset.tab;
                document.getElementById(`${tabId}-tab`).classList.remove('hidden');
            });
        });

        // Like Button Animation
        document.addEventListener('click', (e) => {
            if (e.target.closest('.fa-heart')) {
                const heart = e.target.closest('.fa-heart');
                heart.classList.toggle('far');
                heart.classList.toggle('fas');
                heart.classList.toggle('text-accent');
            }
        });
    </script>
</body>
</html>
