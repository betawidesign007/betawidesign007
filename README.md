<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Profile - betawidesign007 (Web & App Developer)</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Fira+Code:wght@400;500;600&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gh: {
                            bg: '#0d1117',
                            card: '#161b22',
                            border: '#30363d',
                            text: '#c9d1d9',
                            muted: '#8b949e',
                            green: '#238636',
                            greenHover: '#2ea043',
                            blue: '#58a6ff',
                            purple: '#bc8cff',
                            accent: '#1f6feb'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Fira Code', 'monospace']
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #0d1117;
            color: #c9d1d9;
            font-family: 'Inter', sans-serif;
        }
        .gh-tab-active {
            border-bottom: 2px solid #f78166;
            color: #f0f6fc;
            font-weight: 600;
        }
        .glass-card {
            background: rgba(22, 27, 34, 0.8);
            backdrop-filter: blur(8px);
            border: 1px solid #30363d;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0d1117;
        }
        ::-webkit-scrollbar-thumb {
            background: #30363d;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #484f58;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col selection:bg-gh-blue selection:text-black">

    <!-- Top Navigation Bar Header -->
    <header class="bg-[#161b22] border-b border-gh-border px-4 py-3 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <i class="fa-brands fa-github text-3xl text-white"></i>
                <span class="font-semibold text-white tracking-wide text-sm hidden sm:inline">betawidesign007 / Profile Studio</span>
                <span class="bg-purple-900/50 text-gh-purple border border-gh-purple/30 text-xs px-2 py-0.5 rounded-full font-mono">Web & App Developer</span>
            </div>

            <!-- Actions Controls Top -->
            <div class="flex items-center space-x-2">
                <button onclick="openConfigModal()" class="flex items-center space-x-2 bg-gh-border hover:bg-gray-700 text-white text-xs px-3 py-1.5 rounded-md transition font-medium">
                    <i class="fa-solid fa-pen-to-square"></i>
                    <span class="hidden md:inline">Edit Dynamic Content</span>
                </button>
                <button onclick="openMarkdownExportModal()" class="flex items-center space-x-2 bg-gh-green hover:bg-gh-greenHover text-white text-xs px-3 py-1.5 rounded-md font-medium transition shadow-lg">
                    <i class="fa-solid fa-code"></i>
                    <span>Export README.md</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Container -->
    <main class="max-w-7xl w-full mx-auto px-4 py-6 flex-grow">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">

            <!-- LEFT SIDEBAR: PROFILE CARD -->
            <aside class="lg:col-span-4 xl:col-span-3 space-y-4">
                <div class="flex flex-col items-center lg:items-start text-center lg:text-left">
                    <!-- Avatar with Hover Edit Overlay -->
                    <div class="relative group mb-4">
                        <img id="profileAvatar" src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=500&auto=format&fit=crop" 
                             alt="Betawi Design Avatar" 
                             class="w-48 h-48 md:w-56 md:h-56 lg:w-64 lg:h-64 rounded-full border-2 border-gh-border object-cover shadow-xl">
                        <button onclick="changeAvatarPrompt()" class="absolute inset-0 bg-black/60 rounded-full flex flex-col items-center justify-center opacity-0 group-hover:opacity-100 transition duration-200 text-white text-xs font-medium">
                            <i class="fa-solid fa-camera text-xl mb-1"></i>
                            <span>Ubah Foto Profil</span>
                        </button>
                    </div>

                    <!-- Names -->
                    <h1 class="text-2xl font-bold text-white leading-tight" id="profileName">Ibrahim / Betawi Design</h1>
                    <p class="text-gh-muted text-lg font-light mb-3" id="profileUsername">betawidesign007</p>

                    <!-- Customized Quote Card -->
                    <div class="w-full bg-gh-card border border-gh-border p-3 rounded-xl mb-4 text-left relative group">
                        <i class="fa-solid fa-quote-left text-gh-muted opacity-30 text-xs mb-1"></i>
                        <p class="text-xs italic text-gh-text font-mono leading-relaxed" id="sidebarQuote">
                            "Menyulap ide kompleks menjadi aplikasi Web & Mobile yang responsif, cepat, dan elegan."
                        </p>
                        <button onclick="editSidebarQuote()" class="absolute top-2 right-2 text-gh-muted hover:text-white opacity-0 group-hover:opacity-100 transition">
                            <i class="fa-solid fa-pencil text-xs"></i>
                        </button>
                    </div>

                    <!-- HIDDEN FILE INPUT FOR AVATAR -->
                    <input type="file" id="avatarFileInput" accept="image/*" class="hidden" onchange="handleAvatarUpload(event)">

                    <!-- CUSTOM FOLLOW ME BUTTON (Replaces Edit Profile) -->
                    <div class="w-full mb-4">
                        <button id="followBtn" onclick="toggleFollow()" class="w-full flex items-center justify-center space-x-2 bg-[#21262d] hover:bg-[#30363d] border border-gh-border text-white text-sm font-semibold py-2 px-4 rounded-md transition duration-200 group active:scale-95 shadow">
                            <i id="followIcon" class="fa-solid fa-user-plus text-gh-blue group-hover:scale-110 transition"></i>
                            <span id="followText">Follow Me</span>
                            <span id="followerBadge" class="ml-2 bg-gh-border text-xs px-2 py-0.5 rounded-full text-gh-muted group-hover:text-white">1.2k</span>
                        </button>
                    </div>

                    <!-- Bio Details -->
                    <div class="w-full text-xs space-y-2.5 text-gh-muted border-t border-gh-border pt-4 text-left">
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-code text-gh-blue w-4"></i>
                            <span class="text-gh-text font-medium" id="sidebarRole">Full Stack Web & Mobile App Developer</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-location-dot w-4"></i>
                            <span id="sidebarLocation">Jakarta, Indonesia</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-envelope w-4"></i>
                            <a href="mailto:betawidesign007@gmail.com" class="hover:text-gh-blue transition truncate" id="sidebarEmail">betawidesign007@gmail.com</a>
                        </div>
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-globe w-4"></i>
                            <a href="https://github.com/betawidesign007" target="_blank" class="hover:text-gh-blue transition truncate">github.com/betawidesign007</a>
                        </div>
                        <div class="flex items-center space-x-2">
                            <i class="fa-brands fa-linkedin w-4"></i>
                            <span class="hover:text-gh-blue cursor-pointer">@betawidesign007</span>
                        </div>
                    </div>

                    <!-- Achievements Badges -->
                    <div class="w-full border-t border-gh-border pt-4 mt-4 text-left">
                        <h3 class="text-xs font-semibold text-gh-muted mb-2 uppercase tracking-wider">Achievements</h3>
                        <div class="flex flex-wrap gap-2">
                            <span class="inline-flex items-center px-2 py-1 rounded-full text-xs bg-amber-500/10 text-amber-400 border border-amber-500/30" title="Arctic Code Vault Contributor">
                                ❄️ Arctic Code Vault
                            </span>
                            <span class="inline-flex items-center px-2 py-1 rounded-full text-xs bg-purple-500/10 text-purple-400 border border-purple-500/30" title="Pull Shark">
                                🦈 Pull Shark
                            </span>
                            <span class="inline-flex items-center px-2 py-1 rounded-full text-xs bg-blue-500/10 text-blue-400 border border-blue-500/30" title="PRO Developer">
                                ⚡ PRO
                            </span>
                        </div>
                    </div>

                </div>
            </aside>

            <!-- RIGHT MAIN CONTENT AREA -->
            <section class="lg:col-span-8 xl:col-span-9 space-y-6">

                <!-- SUB MENU TABS -->
                <nav class="flex border-b border-gh-border overflow-x-auto space-x-4 sm:space-x-8 text-sm font-medium">
                    <button onclick="switchTab('overview')" id="tab-overview" class="gh-tab-active pb-3 flex items-center space-x-2 whitespace-nowrap">
                        <i class="fa-regular fa-bookmark"></i>
                        <span>Overview</span>
                    </button>
                    <button onclick="switchTab('repositories')" id="tab-repositories" class="text-gh-muted hover:text-white pb-3 flex items-center space-x-2 whitespace-nowrap">
                        <i class="fa-solid fa-book"></i>
                        <span>Repositories</span>
                        <span class="bg-gh-border text-xs px-2 py-0.5 rounded-full">24</span>
                    </button>
                    <button onclick="switchTab('projects')" id="tab-projects" class="text-gh-muted hover:text-white pb-3 flex items-center space-x-2 whitespace-nowrap">
                        <i class="fa-solid fa-[#table-cells]"></i>
                        <i class="fa-solid fa-list-check"></i>
                        <span>Projects Showcase</span>
                    </button>
                    <button onclick="switchTab('packages')" id="tab-packages" class="text-gh-muted hover:text-white pb-3 flex items-center space-x-2 whitespace-nowrap">
                        <i class="fa-solid fa-[#box]"></i>
                        <i class="fa-solid fa-cube"></i>
                        <span>Tech Stack & Packages</span>
                    </button>
                    <button onclick="switchTab('stars')" id="tab-stars" class="text-gh-muted hover:text-white pb-3 flex items-center space-x-2 whitespace-nowrap">
                        <i class="fa-regular fa-star"></i>
                        <span>Stars / Quotes</span>
                        <span class="bg-gh-border text-xs px-2 py-0.5 rounded-full">89</span>
                    </button>
                </nav>

                <!-- TAB CONTENT CONTAINER -->
                <div id="tabContentArea">

                    <!-- HIDDEN FILE INPUT FOR TAB BANNERS -->
                    <input type="file" id="tabBannerFileInput" accept="image/*" class="hidden" onchange="handleTabBannerUpload(event)">

                    <!-- ================= TAB 1: OVERVIEW & SPECIAL README ================= -->
                    <div id="content-overview" class="space-y-6">

                        <!-- SPECIAL GITHUB README CARD -->
                        <div class="bg-gh-card border border-gh-border rounded-xl p-5 md:p-6 shadow-xl relative overflow-hidden">
                            <!-- Background Gradient Glow -->
                            <div class="absolute -top-10 -right-10 w-48 h-48 bg-gh-blue/10 rounded-full filter blur-3xl pointer-events-none"></div>

                            <!-- Header README banner editor -->
                            <div class="flex items-center justify-between border-b border-gh-border pb-3 mb-4">
                                <div class="flex items-center space-x-2 text-xs text-gh-muted font-mono">
                                    <i class="fa-solid fa-book-open text-gh-blue"></i>
                                    <span>betawidesign007 / README.md</span>
                                </div>
                                <span class="text-xs bg-gh-border text-gh-muted px-2 py-0.5 rounded">Special Repository</span>
                            </div>

                            <!-- Interactive Header Banner Image -->
                            <div class="relative group rounded-lg overflow-hidden mb-6 border border-gh-border">
                                <img id="tabHeaderImage-overview" src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=1200&auto=format&fit=crop" 
                                     alt="Banner Web Dev" class="w-full h-44 sm:h-52 object-cover transition duration-300 group-hover:scale-105">
                                <div class="absolute inset-0 bg-gradient-to-t from-gh-bg via-transparent to-transparent"></div>
                                <div class="absolute bottom-4 left-4 right-4 flex justify-between items-end">
                                    <div>
                                        <h2 class="text-xl sm:text-2xl font-bold text-white drop-shadow-md">Web & Mobile Application Architect</h2>
                                        <p class="text-xs sm:text-sm text-gh-blue font-mono drop-shadow">Building digital experiences with modern code.</p>
                                    </div>
                                    <button onclick="triggerTabImageUpload('overview')" class="bg-black/70 hover:bg-black text-white text-xs px-3 py-1.5 rounded-md backdrop-blur border border-white/20 opacity-0 group-hover:opacity-100 transition flex items-center space-x-1.5">
                                        <i class="fa-solid fa-upload"></i>
                                        <span>Upload Banner Lokal</span>
                                    </button>
                                </div>
                            </div>

                            <!-- Section Quote Block -->
                            <div class="bg-gh-bg border-l-4 border-gh-purple p-4 rounded-r-lg mb-6 relative group">
                                <p class="text-sm font-mono text-gh-text italic" id="tabQuote-overview">
                                    "Kreativitas berpadu dengan fungsionalitas. Setiap baris kode ditulis untuk memberikan solusi dunia nyata."
                                </p>
                                <button onclick="editTabQuote('overview')" class="absolute top-2 right-2 text-gh-muted hover:text-white opacity-0 group-hover:opacity-100 transition">
                                    <i class="fa-solid fa-pencil text-xs"></i>
                                </button>
                            </div>

                            <!-- Interactive Tech Stack Matrix -->
                            <div class="mb-6">
                                <h3 class="text-xs font-semibold text-gh-muted uppercase tracking-wider mb-3">⚡ Tech Stack & Ecosystem</h3>
                                <div class="grid grid-cols-2 sm:grid-cols-4 gap-3 text-xs font-mono">
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-gh-blue transition">
                                        <i class="fa-brands fa-react text-cyan-400 text-lg"></i>
                                        <span>React / Next.js</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-red-500 transition">
                                        <i class="fa-brands fa-laravel text-red-500 text-lg"></i>
                                        <span>Laravel / PHP</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-emerald-400 transition">
                                        <i class="fa-brands fa-node-js text-emerald-400 text-lg"></i>
                                        <span>Node.js / Express</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-blue-400 transition">
                                        <i class="fa-solid fa-mobile-screen-button text-blue-400 text-lg"></i>
                                        <span>Flutter / Mobile</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-teal-400 transition">
                                        <i class="fa-brands fa-css3-alt text-teal-400 text-lg"></i>
                                        <span>Tailwind CSS</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-yellow-400 transition">
                                        <i class="fa-brands fa-python text-yellow-400 text-lg"></i>
                                        <span>Python</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-blue-600 transition">
                                        <i class="fa-solid fa-database text-blue-600 text-lg"></i>
                                        <span>MySQL / Postgres</span>
                                    </div>
                                    <div class="p-2.5 rounded-lg bg-[#0d1117] border border-gh-border flex items-center space-x-2.5 hover:border-purple-400 transition">
                                        <i class="fa-brands fa-docker text-purple-400 text-lg"></i>
                                        <span>Docker / CI-CD</span>
                                    </div>
                                </div>
                            </div>

                            <!-- GitHub Dynamic Stats Visualizer Mockup -->
                            <div>
                                <h3 class="text-xs font-semibold text-gh-muted uppercase tracking-wider mb-3">📊 GitHub Analytics Dashboard</h3>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                    <!-- Card 1 -->
                                    <div class="p-4 rounded-lg bg-[#0d1117] border border-gh-border flex flex-col justify-between space-y-3">
                                        <div class="flex justify-between items-center text-xs text-gh-muted border-b border-gh-border/50 pb-2">
                                            <span class="font-semibold text-white">betawidesign007's Stats</span>
                                            <i class="fa-solid fa-chart-line text-gh-blue"></i>
                                        </div>
                                        <div class="grid grid-cols-2 gap-2 text-xs">
                                            <div>
                                                <span class="text-gh-muted block">Total Commits</span>
                                                <span class="text-lg font-bold text-white font-mono">1,482</span>
                                            </div>
                                            <div>
                                                <span class="text-gh-muted block">Pull Requests</span>
                                                <span class="text-lg font-bold text-gh-purple font-mono">194</span>
                                            </div>
                                            <div>
                                                <span class="text-gh-muted block">Total PR Stars</span>
                                                <span class="text-lg font-bold text-yellow-400 font-mono">312</span>
                                            </div>
                                            <div>
                                                <span class="text-gh-muted block">Contributed To</span>
                                                <span class="text-lg font-bold text-gh-green font-mono">38 Repos</span>
                                            </div>
                                        </div>
                                    </div>

                                    <!-- Card 2 Languages -->
                                    <div class="p-4 rounded-lg bg-[#0d1117] border border-gh-border flex flex-col justify-between">
                                        <div class="flex justify-between items-center text-xs text-gh-muted border-b border-gh-border/50 pb-2">
                                            <span class="font-semibold text-white">Most Used Languages</span>
                                            <i class="fa-solid fa-code-commit text-gh-purple"></i>
                                        </div>
                                        <div class="space-y-2 py-1">
                                            <div>
                                                <div class="flex justify-between text-xs mb-1">
                                                    <span>JavaScript / TypeScript</span>
                                                    <span class="text-gh-muted">45%</span>
                                                </div>
                                                <div class="w-full bg-gh-border h-1.5 rounded-full overflow-hidden">
                                                    <div class="bg-yellow-400 h-full w-[45%]"></div>
                                                </div>
                                            </div>
                                            <div>
                                                <div class="flex justify-between text-xs mb-1">
                                                    <span>PHP / Laravel</span>
                                                    <span class="text-gh-muted">30%</span>
                                                </div>
                                                <div class="w-full bg-gh-border h-1.5 rounded-full overflow-hidden">
                                                    <div class="bg-purple-500 h-full w-[30%]"></div>
                                                </div>
                                            </div>
                                            <div>
                                                <div class="flex justify-between text-xs mb-1">
                                                    <span>Dart / Flutter</span>
                                                    <span class="text-gh-muted">15%</span>
                                                </div>
                                                <div class="w-full bg-gh-border h-1.5 rounded-full overflow-hidden">
                                                    <div class="bg-blue-400 h-full w-[15%]"></div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                        </div>

                        <!-- Pinned Repositories Section -->
                        <div>
                            <h3 class="text-sm font-semibold text-white mb-3 flex items-center justify-between">
                                <span>Pinned Featured Projects</span>
                                <span class="text-xs text-gh-muted font-normal">Customized view</span>
                            </h3>

                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <!-- Pinned Item 1 -->
                                <div class="bg-gh-card border border-gh-border rounded-lg p-4 hover:border-gh-muted transition flex flex-col justify-between space-y-3">
                                    <div>
                                        <div class="flex items-center justify-between mb-1">
                                            <a href="#" class="text-gh-blue font-semibold text-sm hover:underline flex items-center space-x-2">
                                                <i class="fa-regular fa-bookmark text-gh-muted"></i>
                                                <span>smart-pos-system</span>
                                            </a>
                                            <span class="text-xs border border-gh-border px-2 py-0.5 rounded-full text-gh-muted">Public</span>
                                        </div>
                                        <p class="text-xs text-gh-muted line-clamp-2">Aplikasi Kasir (POS) berbasis Web & PWA modern dengan sync offline-online, manajemen stok, dan laporan keuangan realtime.</p>
                                    </div>
                                    <div class="flex items-center space-x-4 text-xs text-gh-muted">
                                        <span class="flex items-center space-x-1">
                                            <span class="w-3 h-3 rounded-full bg-yellow-400 inline-block"></span>
                                            <span>Vue / Node</span>
                                        </span>
                                        <span class="hover:text-gh-blue cursor-pointer"><i class="fa-regular fa-star mr-1"></i>42</span>
                                        <span class="hover:text-gh-blue cursor-pointer"><i class="fa-solid fa-code-branch mr-1"></i>12</span>
                                    </div>
                                </div>

                                <!-- Pinned Item 2 -->
                                <div class="bg-gh-card border border-gh-border rounded-lg p-4 hover:border-gh-muted transition flex flex-col justify-between space-y-3">
                                    <div>
                                        <div class="flex items-center justify-between mb-1">
                                            <a href="#" class="text-gh-blue font-semibold text-sm hover:underline flex items-center space-x-2">
                                                <i class="fa-regular fa-bookmark text-gh-muted"></i>
                                                <span>mobile-fleet-tracker</span>
                                            </a>
                                            <span class="text-xs border border-gh-border px-2 py-0.5 rounded-full text-gh-muted">Public</span>
                                        </div>
                                        <p class="text-xs text-gh-muted line-clamp-2">Aplikasi Mobile Flutter pelacak armada kendaraan realtime menggunakan WebSockets dan Geofencing maps API.</p>
                                    </div>
                                    <div class="flex items-center space-x-4 text-xs text-gh-muted">
                                        <span class="flex items-center space-x-1">
                                            <span class="w-3 h-3 rounded-full bg-blue-500 inline-block"></span>
                                            <span>Flutter</span>
                                        </span>
                                        <span class="hover:text-gh-blue cursor-pointer"><i class="fa-regular fa-star mr-1"></i>38</span>
                                        <span class="hover:text-gh-blue cursor-pointer"><i class="fa-solid fa-code-branch mr-1"></i>8</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                    </div>

                    <!-- ================= TAB 2: REPOSITORIES ================= -->
                    <div id="content-repositories" class="hidden space-y-4">
                        <!-- Custom Section Quote Header -->
                        <div class="bg-gh-card border border-gh-border p-4 rounded-xl relative group">
                            <div class="flex items-start space-x-3">
                                <img id="tabHeaderImage-repositories" src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=300&auto=format&fit=crop" 
                                     alt="Repo Header" class="w-16 h-16 rounded-lg object-cover border border-gh-border">
                                <div class="flex-grow">
                                    <h3 class="text-sm font-semibold text-white">Open Source & Repository Hub</h3>
                                    <p class="text-xs italic text-gh-muted font-mono mt-1" id="tabQuote-repositories">
                                        "Kode yang bersih adalah dokumentasi terbaik. Jelajahi repositori publik saya di bawah ini."
                                    </p>
                                </div>
                            </div>
                            <div class="absolute top-2 right-2 flex space-x-1 opacity-0 group-hover:opacity-100 transition">
                                <button onclick="editTabQuote('repositories')" class="text-gh-muted hover:text-white p-1" title="Edit Quote">
                                    <i class="fa-solid fa-pencil text-xs"></i>
                                </button>
                                <button onclick="triggerTabImageUpload('repositories')" class="text-gh-muted hover:text-white p-1" title="Upload Gambar Baru">
                                    <i class="fa-solid fa-upload text-xs"></i>
                                </button>
                            </div>
                        </div>

                        <!-- Search & Filter Bar -->
                        <div class="flex flex-col sm:flex-row gap-2 border-b border-gh-border pb-4">
                            <input type="text" placeholder="Find a repository..." class="bg-[#0d1117] border border-gh-border text-xs rounded-md px-3 py-2 text-white focus:outline-none focus:border-gh-blue flex-grow">
                            <div class="flex gap-2">
                                <button class="bg-gh-card border border-gh-border text-xs px-3 py-2 rounded-md text-gh-text hover:bg-gh-border">Type: All</button>
                                <button class="bg-gh-card border border-gh-border text-xs px-3 py-2 rounded-md text-gh-text hover:bg-gh-border">Language: All</button>
                            </div>
                        </div>

                        <!-- Repo List Items -->
                        <div class="divide-y divide-gh-border" id="repoList">
                            <!-- JS will populate dynamic repos or mock -->
                            <div class="py-4 flex justify-between items-start">
                                <div>
                                    <div class="flex items-center space-x-2">
                                        <a href="#" class="text-gh-blue font-semibold text-base hover:underline">betawidesign007-portfolio</a>
                                        <span class="text-xs border border-gh-border px-2 py-0.5 rounded-full text-gh-muted">Public</span>
                                    </div>
                                    <p class="text-xs text-gh-muted mt-1 max-w-2xl">Interactive dark-themed GitHub profile clone & portfolio generator application built for high visual impact.</p>
                                    <div class="flex items-center space-x-4 text-xs text-gh-muted mt-3">
                                        <span class="flex items-center space-x-1"><span class="w-3 h-3 rounded-full bg-yellow-400"></span><span>HTML/Tailwind</span></span>
                                        <span>Updated 2 hours ago</span>
                                    </div>
                                </div>
                                <button class="bg-[#21262d] border border-gh-border hover:bg-[#30363d] text-xs px-3 py-1 rounded-md text-gh-text"><i class="fa-regular fa-star mr-1"></i> Star</button>
                            </div>

                            <div class="py-4 flex justify-between items-start">
                                <div>
                                    <div class="flex items-center space-x-2">
                                        <a href="#" class="text-gh-blue font-semibold text-base hover:underline">laravel-ecommerce-api</a>
                                        <span class="text-xs border border-gh-border px-2 py-0.5 rounded-full text-gh-muted">Public</span>
                                    </div>
                                    <p class="text-xs text-gh-muted mt-1 max-w-2xl">RESTful API backend scalable ecommerce dengan integrasi Payment Gateway Midtrans & Xendit.</p>
                                    <div class="flex items-center space-x-4 text-xs text-gh-muted mt-3">
                                        <span class="flex items-center space-x-1"><span class="w-3 h-3 rounded-full bg-purple-500"></span><span>PHP</span></span>
                                        <span>Updated 3 days ago</span>
                                    </div>
                                </div>
                                <button class="bg-[#21262d] border border-gh-border hover:bg-[#30363d] text-xs px-3 py-1 rounded-md text-gh-text"><i class="fa-regular fa-star mr-1"></i> Star</button>
                            </div>
                        </div>
                    </div>

                    <!-- ================= TAB 3: PROJECTS SHOWCASE ================= -->
                    <div id="content-projects" class="hidden space-y-6">
                        <!-- Custom Section Quote Header -->
                        <div class="bg-gh-card border border-gh-border p-4 rounded-xl relative group">
                            <div class="flex items-start space-x-3">
                                <img id="tabHeaderImage-projects" src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80&w=300&auto=format&fit=crop" 
                                     alt="Projects Header" class="w-16 h-16 rounded-lg object-cover border border-gh-border">
                                <div class="flex-grow">
                                    <h3 class="text-sm font-semibold text-white">App & Web Development Showcase</h3>
                                    <p class="text-xs italic text-gh-muted font-mono mt-1" id="tabQuote-projects">
                                        "Portfolio aplikasi nyata yang siap pakai, berdampak tinggi, dan dirancang presisi."
                                    </p>
                                </div>
                            </div>
                            <div class="absolute top-2 right-2 flex space-x-1 opacity-0 group-hover:opacity-100 transition">
                                <button onclick="editTabQuote('projects')" class="text-gh-muted hover:text-white p-1" title="Edit Quote">
                                    <i class="fa-solid fa-pencil text-xs"></i>
                                </button>
                                <button onclick="triggerTabImageUpload('projects')" class="text-gh-muted hover:text-white p-1" title="Upload Gambar Baru">
                                    <i class="fa-solid fa-upload text-xs"></i>
                                </button>
                            </div>
                        </div>

                        <!-- Cards Grid Projects -->
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- Project Card 1 -->
                            <div class="bg-gh-card border border-gh-border rounded-xl overflow-hidden hover:border-gh-blue transition group">
                                <div class="h-40 overflow-hidden relative">
                                    <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?q=80&w=600&auto=format&fit=crop" alt="Dashboard SaaS" class="w-full h-full object-cover group-hover:scale-105 transition duration-300">
                                    <div class="absolute top-2 right-2 bg-black/70 backdrop-blur text-xs px-2 py-1 rounded text-gh-blue font-mono">SaaS / Web App</div>
                                </div>
                                <div class="p-4 space-y-2">
                                    <h4 class="font-bold text-white text-base group-hover:text-gh-blue transition">Analytics Enterprise Dashboard</h4>
                                    <p class="text-xs text-gh-muted">Platform visualisasi data transaksi bisnis secara real-time dengan grafik interaktif dan ekspor laporan PDF/Excel.</p>
                                    <div class="pt-2 flex flex-wrap gap-1 text-[11px] font-mono">
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">Next.js</span>
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">TailwindCSS</span>
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">Chart.js</span>
                                    </div>
                                </div>
                            </div>

                            <!-- Project Card 2 -->
                            <div class="bg-gh-card border border-gh-border rounded-xl overflow-hidden hover:border-gh-purple transition group">
                                <div class="h-40 overflow-hidden relative">
                                    <img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?q=80&w=600&auto=format&fit=crop" alt="Mobile App" class="w-full h-full object-cover group-hover:scale-105 transition duration-300">
                                    <div class="absolute top-2 right-2 bg-black/70 backdrop-blur text-xs px-2 py-1 rounded text-gh-purple font-mono">Mobile iOS & Android</div>
                                </div>
                                <div class="p-4 space-y-2">
                                    <h4 class="font-bold text-white text-base group-hover:text-gh-purple transition">Food Delivery & Courier App</h4>
                                    <p class="text-xs text-gh-muted">Aplikasi seluler pemesanan makanan cepat saji berbasis lokasi GPS lengkap dengan fitur tracking kurir langsung.</p>
                                    <div class="pt-2 flex flex-wrap gap-1 text-[11px] font-mono">
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">Flutter</span>
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">Firebase</span>
                                        <span class="bg-gh-bg border border-gh-border px-2 py-0.5 rounded text-gh-text">Google Maps API</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- ================= TAB 4: PACKAGES & SKILLS ================= -->
                    <div id="content-packages" class="hidden space-y-6">
                        <!-- Custom Section Quote Header -->
                        <div class="bg-gh-card border border-gh-border p-4 rounded-xl relative group">
                            <div class="flex items-start space-x-3">
                                <img id="tabHeaderImage-packages" src="https://images.unsplash.com/photo-1542831371-29b0f74f9713?q=80&w=300&auto=format&fit=crop" 
                                     alt="Packages Header" class="w-16 h-16 rounded-lg object-cover border border-gh-border">
                                <div class="flex-grow">
                                    <h3 class="text-sm font-semibold text-white">Development Packages & Services</h3>
                                    <p class="text-xs italic text-gh-muted font-mono mt-1" id="tabQuote-packages">
                                        "Layanan profesional dari konsep desain wireframe hingga deployment server cloud."
                                    </p>
                                </div>
                            </div>
                            <div class="absolute top-2 right-2 flex space-x-1 opacity-0 group-hover:opacity-100 transition">
                                <button onclick="editTabQuote('packages')" class="text-gh-muted hover:text-white p-1" title="Edit Quote">
                                    <i class="fa-solid fa-pencil text-xs"></i>
                                </button>
                                <button onclick="triggerTabImageUpload('packages')" class="text-gh-muted hover:text-white p-1" title="Upload Gambar Baru">
                                    <i class="fa-solid fa-upload text-xs"></i>
                                </button>
                            </div>
                        </div>

                        <!-- Service Offerings Packages -->
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <div class="bg-gh-card border border-gh-border p-5 rounded-xl space-y-3 relative overflow-hidden">
                                <div class="text-gh-blue text-2xl"><i class="fa-solid fa-laptop-code"></i></div>
                                <h4 class="text-base font-bold text-white">Web Application</h4>
                                <ul class="text-xs text-gh-muted space-y-1.5 list-disc list-inside">
                                    <li>Custom Single Page App (SPA)</li>
                                    <li>Company Profile Premium</li>
                                    <li>Dashboard System / Admin</li>
                                    <li>RESTful API & Integration</li>
                                </ul>
                            </div>

                            <div class="bg-gh-card border border-gh-border p-5 rounded-xl space-y-3 relative overflow-hidden">
                                <div class="text-gh-purple text-2xl"><i class="fa-solid fa-mobile-screen"></i></div>
                                <h4 class="text-base font-bold text-white">Mobile Application</h4>
                                <ul class="text-xs text-gh-muted space-y-1.5 list-disc list-inside">
                                    <li>Cross-platform iOS & Android</li>
                                    <li>Flutter App Development</li>
                                    <li>Offline-First Database</li>
                                    <li>Playstore & AppStore Publish</li>
                                </ul>
                            </div>

                            <div class="bg-gh-card border border-gh-border p-5 rounded-xl space-y-3 relative overflow-hidden">
                                <div class="text-gh-green text-2xl"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                                <h4 class="text-base font-bold text-white">UI/UX & Redesign</h4>
                                <ul class="text-xs text-gh-muted space-y-1.5 list-disc list-inside">
                                    <li>Figma Prototype & Design</li>
                                    <li>Responsive Modern Redesign</li>
                                    <li>Performance Optimization</li>
                                    <li>SEO & Accessibility</li>
                                </ul>
                            </div>
                        </div>
                    </div>

                    <!-- ================= TAB 5: STARS & QUOTES ================= -->
                    <div id="content-stars" class="hidden space-y-6">
                        <!-- Custom Section Quote Header -->
                        <div class="bg-gh-card border border-gh-border p-4 rounded-xl relative group">
                            <div class="flex items-start space-x-3">
                                <img id="tabHeaderImage-stars" src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?q=80&w=300&auto=format&fit=crop" 
                                     alt="Stars Header" class="w-16 h-16 rounded-lg object-cover border border-gh-border">
                                <div class="flex-grow">
                                    <h3 class="text-sm font-semibold text-white">Developer Quotes & Philosophy</h3>
                                    <p class="text-xs italic text-gh-muted font-mono mt-1" id="tabQuote-stars">
                                        "Teknologi terbaik adalah teknologi yang mempermudah hidup manusia."
                                    </p>
                                </div>
                            </div>
                            <div class="absolute top-2 right-2 flex space-x-1 opacity-0 group-hover:opacity-100 transition">
                                <button onclick="editTabQuote('stars')" class="text-gh-muted hover:text-white p-1" title="Edit Quote">
                                    <i class="fa-solid fa-pencil text-xs"></i>
                                </button>
                                <button onclick="triggerTabImageUpload('stars')" class="text-gh-muted hover:text-white p-1" title="Upload Gambar Baru">
                                    <i class="fa-solid fa-upload text-xs"></i>
                                </button>
                            </div>
                        </div>

                        <!-- Quotes Cards Grid -->
                        <div class="space-y-4">
                            <div class="bg-gh-card border border-gh-border p-4 rounded-xl flex space-x-4 items-start">
                                <div class="text-3xl text-gh-blue opacity-50"><i class="fa-solid fa-quote-left"></i></div>
                                <div class="space-y-1">
                                    <p class="text-sm font-mono text-gh-text">"First, solve the problem. Then, write the code."</p>
                                    <span class="text-xs text-gh-muted block">- John Johnson</span>
                                </div>
                            </div>

                            <div class="bg-gh-card border border-gh-border p-4 rounded-xl flex space-x-4 items-start">
                                <div class="text-3xl text-gh-purple opacity-50"><i class="fa-solid fa-quote-left"></i></div>
                                <div class="space-y-1">
                                    <p class="text-sm font-mono text-gh-text">"Simplicity is the soul of efficiency."</p>
                                    <span class="text-xs text-gh-muted block">- Austin Freeman</span>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </section>
        </div>
    </main>

    <!-- Footer -->
    <footer class="border-t border-gh-border bg-gh-card mt-12 py-6 text-center text-xs text-gh-muted">
        <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row justify-between items-center space-y-2 sm:space-y-0">
            <div class="flex items-center space-x-2">
                <i class="fa-brands fa-github text-lg text-white"></i>
                <span>&copy; 2026 betawidesign007. GitHub Profile Enhanced.</span>
            </div>
            <div class="flex space-x-4">
                <a href="https://github.com/betawidesign007" target="_blank" class="hover:text-gh-blue">GitHub Profile</a>
                <a href="#" onclick="openMarkdownExportModal()" class="hover:text-gh-blue">Get Markdown Code</a>
            </div>
        </div>
    </footer>

    <!-- MODAL 1: EDIT CONFIGURATION / TEXT / QUOTE -->
    <div id="configModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm hidden items-center justify-center p-4 z-50">
        <div class="bg-gh-card border border-gh-border w-full max-w-lg rounded-xl p-6 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-gh-border pb-3">
                <h3 class="text-base font-bold text-white flex items-center space-x-2">
                    <i class="fa-solid fa-sliders text-gh-blue"></i>
                    <span>Edit Profile Details</span>
                </h3>
                <button onclick="closeConfigModal()" class="text-gh-muted hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            
            <div class="space-y-3 text-xs">
                <div>
                    <label class="block text-gh-muted mb-1 font-medium">Display Name</label>
                    <input type="text" id="inputName" class="w-full bg-gh-bg border border-gh-border rounded p-2 text-white focus:outline-none focus:border-gh-blue">
                </div>
                <div>
                    <label class="block text-gh-muted mb-1 font-medium">Role / Title</label>
                    <input type="text" id="inputRole" class="w-full bg-gh-bg border border-gh-border rounded p-2 text-white focus:outline-none focus:border-gh-blue">
                </div>
                <div>
                    <label class="block text-gh-muted mb-1 font-medium">Sidebar Quote / Motto</label>
                    <textarea id="inputQuote" rows="2" class="w-full bg-gh-bg border border-gh-border rounded p-2 text-white focus:outline-none focus:border-gh-blue"></textarea>
                </div>
                <div>
                    <label class="block text-gh-muted mb-1 font-medium">Lokasi</label>
                    <input type="text" id="inputLocation" class="w-full bg-gh-bg border border-gh-border rounded p-2 text-white focus:outline-none focus:border-gh-blue">
                </div>
            </div>

            <div class="flex justify-end space-x-2 border-t border-gh-border pt-4">
                <button onclick="closeConfigModal()" class="px-4 py-1.5 rounded bg-gh-border text-xs text-white hover:bg-gray-700">Batal</button>
                <button onclick="saveConfig()" class="px-4 py-1.5 rounded bg-gh-green text-xs text-white hover:bg-gh-greenHover font-semibold">Simpan Perubahan</button>
            </div>
        </div>
    </div>

    <!-- MODAL 2: EXPORT MARKDOWN README FOR REAL GITHUB -->
    <div id="markdownModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm hidden items-center justify-center p-4 z-50">
        <div class="bg-gh-card border border-gh-border w-full max-w-2xl rounded-xl p-6 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-gh-border pb-3">
                <div class="flex items-center space-x-2">
                    <i class="fa-brands fa-markdown text-2xl text-gh-blue"></i>
                    <div>
                        <h3 class="text-base font-bold text-white leading-none">README.md Markdown Code</h3>
                        <span class="text-xs text-gh-muted">Copy dan paste kode ini ke repo `betawidesign007/betawidesign007` Anda</span>
                    </div>
                </div>
                <button onclick="closeMarkdownModal()" class="text-gh-muted hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>

            <div class="relative">
                <textarea id="markdownCode" readonly rows="12" class="w-full bg-gh-bg border border-gh-border rounded-lg p-3 text-xs font-mono text-gh-text focus:outline-none resize-none selection:bg-gh-blue selection:text-black"></textarea>
                <button onclick="copyMarkdownCode()" class="absolute top-3 right-3 bg-gh-border hover:bg-gray-700 text-white text-xs px-3 py-1.5 rounded flex items-center space-x-1 shadow">
                    <i class="fa-regular fa-copy"></i>
                    <span id="copyBtnText">Salin Kode</span>
                </button>
            </div>

            <div class="bg-gh-bg border border-gh-border p-3 rounded-lg text-xs text-gh-muted flex items-start space-x-2">
                <i class="fa-solid fa-circle-info text-gh-blue text-sm mt-0.5"></i>
                <div>
                    <strong class="text-white">Cara Menggunakan:</strong> Buat repositori baru bernama <code class="text-gh-purple">betawidesign007</code> (harus sama persis dengan username), lalu buat file <code class="text-gh-purple">README.md</code> dan paste kode di atas.
                </div>
            </div>

            <div class="flex justify-end">
                <button onclick="closeMarkdownModal()" class="px-4 py-1.5 rounded bg-gh-border text-xs text-white hover:bg-gray-700">Tutup</button>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT APPLICATION LOGIC -->
    <script>
        // State variables
        let isFollowing = false;
        let followerCount = 1200;
        let activeTabForUpload = null;

        // Trigger Local File Picker for Avatar
        function changeAvatarPrompt() {
            document.getElementById('avatarFileInput').click();
        }

        function handleAvatarUpload(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('profileAvatar').src = e.target.result;
                };
                reader.readAsDataURL(file);
            }
        }

        // Trigger Local File Picker for Sub-Menu Tab Banner Images
        function triggerTabImageUpload(tabKey) {
            activeTabForUpload = tabKey;
            document.getElementById('tabBannerFileInput').click();
        }

        function handleTabBannerUpload(event) {
            const file = event.target.files[0];
            if (file && activeTabForUpload) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const imgElem = document.getElementById(`tabHeaderImage-${activeTabForUpload}`);
                    if (imgElem) {
                        imgElem.src = e.target.result;
                    }
                };
                reader.readAsDataURL(file);
            }
        }

        // Interactive Follow Toggle
        function toggleFollow() {
            const btn = document.getElementById('followBtn');
            const icon = document.getElementById('followIcon');
            const text = document.getElementById('followText');
            const badge = document.getElementById('followerBadge');

            isFollowing = !isFollowing;

            if (isFollowing) {
                followerCount++;
                btn.classList.remove('bg-[#21262d]', 'hover:bg-[#30363d]');
                btn.classList.add('bg-gh-border', 'border-gh-muted');
                icon.className = 'fa-solid fa-user-check text-gh-green';
                text.innerText = 'Following';
            } else {
                followerCount--;
                btn.classList.remove('bg-gh-border', 'border-gh-muted');
                btn.classList.add('bg-[#21262d]', 'hover:bg-[#30363d]');
                icon.className = 'fa-solid fa-user-plus text-gh-blue';
                text.innerText = 'Follow Me';
            }
            badge.innerText = followerCount >= 1000 ? (followerCount/1000).toFixed(1) + 'k' : followerCount;
        }

        // Tab Switching Logic
        function switchTab(tabId) {
            const tabs = ['overview', 'repositories', 'projects', 'packages', 'stars'];
            
            tabs.forEach(t => {
                const tabBtn = document.getElementById(`tab-${t}`);
                const content = document.getElementById(`content-${t}`);
                
                if (t === tabId) {
                    tabBtn.className = 'gh-tab-active pb-3 flex items-center space-x-2 whitespace-nowrap';
                    content.classList.remove('hidden');
                } else {
                    tabBtn.className = 'text-gh-muted hover:text-white pb-3 flex items-center space-x-2 whitespace-nowrap';
                    content.classList.add('hidden');
                }
            });
        }

        // Inline Quote Editor for specific Tab
        function editTabQuote(tabKey) {
            const quoteElem = document.getElementById(`tabQuote-${tabKey}`);
            if (quoteElem) {
                const currentText = quoteElem.innerText.replace(/"/g, '');
                const newQuote = prompt("Edit Kutipan / Quote untuk Tab ini:", currentText);
                if (newQuote !== null) {
                    quoteElem.innerText = `"${newQuote}"`;
                }
            }
        }

        // Sidebar Quote Editor
        function editSidebarQuote() {
            const quoteElem = document.getElementById('sidebarQuote');
            const currentText = quoteElem.innerText.replace(/"/g, '');
            const newQuote = prompt("Edit Sidebar Quote:", currentText);
            if (newQuote !== null) {
                quoteElem.innerText = `"${newQuote}"`;
            }
        }

        // Config Modal Trigger
        function openConfigModal() {
            document.getElementById('inputName').value = document.getElementById('profileName').innerText;
            document.getElementById('inputRole').value = document.getElementById('sidebarRole').innerText;
            document.getElementById('inputQuote').value = document.getElementById('sidebarQuote').innerText.replace(/"/g, '');
            document.getElementById('inputLocation').value = document.getElementById('sidebarLocation').innerText;

            document.getElementById('configModal').classList.remove('hidden');
            document.getElementById('configModal').classList.add('flex');
        }

        function closeConfigModal() {
            document.getElementById('configModal').classList.add('hidden');
            document.getElementById('configModal').classList.remove('flex');
        }

        function saveConfig() {
            document.getElementById('profileName').innerText = document.getElementById('inputName').value;
            document.getElementById('sidebarRole').innerText = document.getElementById('inputRole').value;
            document.getElementById('sidebarQuote').innerText = `"${document.getElementById('inputQuote').value}"`;
            document.getElementById('sidebarLocation').innerText = document.getElementById('inputLocation').value;
            closeConfigModal();
        }

        // Export Real Markdown README Generation
        function openMarkdownExportModal() {
            const name = document.getElementById('profileName').innerText;
            const role = document.getElementById('sidebarRole').innerText;
            const quote = document.getElementById('sidebarQuote').innerText;
            const location = document.getElementById('sidebarLocation').innerText;

            const markdownTemplate = 
`<h1 align="center">Hi 👋, I'm ${name}</h1>
<h3 align="center">🚀 ${role} from ${location}</h3>

<p align="center">
  <em>${quote}</em>
</p>

---

### ⚡ Tech Stack & Tools
<p align="left">
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white" />
</p>

---

### 📊 GitHub Dynamic Statistics

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=betawidesign007&show_icons=true&theme=dark&count_private=true" width="48%" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=betawidesign007&layout=compact&theme=dark" width="48%" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=betawidesign007&theme=dark" width="97%" />
</p>

---

### 📫 Connect with Me
- 🌐 GitHub: [github.com/betawidesign007](https://github.com/betawidesign007)
- ✉️ Email: [betawidesign007@gmail.com](mailto:betawidesign007@gmail.com)

> *"Turning ideas into scalable Web & Mobile applications."*
`;

            document.getElementById('markdownCode').value = markdownTemplate;
            document.getElementById('markdownModal').classList.remove('hidden');
            document.getElementById('markdownModal').classList.add('flex');
        }

        function closeMarkdownModal() {
            document.getElementById('markdownModal').classList.add('hidden');
            document.getElementById('markdownModal').classList.remove('flex');
        }

        function copyMarkdownCode() {
            const textarea = document.getElementById('markdownCode');
            textarea.select();
            document.execCommand('copy');

            const btnText = document.getElementById('copyBtnText');
            btnText.innerText = 'Tersalin!';
            setTimeout(() => {
                btnText.innerText = 'Salin Kode';
            }, 2000);
        }
    </script>
</body>
</html>
