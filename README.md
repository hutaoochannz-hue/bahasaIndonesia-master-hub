<!DOCTYPE html>
<html lang="id" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Belajar B.Indonesia Kelas X | SMAN 4 Kendari</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Plus Jakarta Sans & Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        sman4: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            500: '#3b82f6',
                            600: '#2563eb',
                            700: '#1d4ed8',
                            800: '#1e3a8a', // Royal Navy SMAN 4
                            900: '#172554',
                        },
                        emas: {
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom Scrollbar & 3D Flip Utilities */
        body {
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
        }
        h1, h2, h3, h4, .font-display {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0.2, 0.2, 1);
        }
        .backface-hidden {
            backface-visibility: hidden;
            -webkit-backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }
        /* Highlight badge styling in example texts */
        .hl-tag {
            display: inline-block;
            font-size: 0.7rem;
            font-weight: 700;
            padding: 1px 6px;
            border-radius: 4px;
            margin-right: 4px;
            text-transform: uppercase;
            letter-spacing: 0.03em;
            vertical-align: middle;
        }
        /* Smooth fade in */
        .fade-in {
            animation: fadeIn 0.3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(148, 163, 184, 0.4);
            border-radius: 9999px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: rgba(100, 116, 139, 0.6);
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 dark:bg-slate-950 dark:text-slate-100 transition-colors duration-200 min-h-screen flex flex-col">

    <!-- Toast Notification Container (Replaces alert) -->
    <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 pointer-events-none"></div>

    <!-- Top Navigation & School Banner -->
    <header class="sticky top-0 z-40 bg-white/90 dark:bg-slate-900/90 backdrop-blur-md border-b border-slate-200 dark:border-slate-800 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between gap-4">
            <!-- Brand / SMAN 4 Kendari Identity -->
            <div class="flex items-center gap-3">
                <button id="mobile-menu-btn" class="lg:hidden p-2 rounded-xl text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800">
                    <i data-lucide="menu" class="w-6 h-6"></i>
                </button>
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-sman4-800 to-indigo-600 flex items-center justify-center text-emas-400 shadow-md shrink-0 border border-emas-400/30">
                    <i data-lucide="graduation-cap" class="w-6 h-6"></i>
                </div>
                <div>
                    <div class="flex items-center gap-2">
                        <span class="font-display font-extrabold text-base sm:text-lg tracking-tight text-sman4-800 dark:text-white">SMAN 4 KENDARI</span>
                        <span class="hidden sm:inline-flex items-center px-2 py-0.5 rounded-full text-xs font-semibold bg-emas-400/20 text-emas-600 dark:text-emas-400 border border-emas-400/30">Kelas X</span>
                    </div>
                    <p class="text-xs text-slate-500 dark:text-slate-400 truncate">Dashboard Persiapan Ulangan Bahasa Indonesia</p>
                </div>
            </div>

            <!-- Quick Stats & Dark Mode Toggle -->
            <div class="flex items-center gap-2 sm:gap-4">
                <div class="hidden md:flex items-center gap-3 bg-slate-100 dark:bg-slate-800/80 px-3.5 py-1.5 rounded-xl border border-slate-200/70 dark:border-slate-700/70 text-xs">
                    <div class="flex items-center gap-1.5" title="Materi Dipelajari">
                        <i data-lucide="book-open-check" class="w-4 h-4 text-emerald-500"></i>
                        <span class="text-slate-500 dark:text-slate-400">Materi:</span>
                        <span id="stat-materi-top" class="font-bold text-slate-800 dark:text-white">0/4</span>
                    </div>
                    <span class="text-slate-300 dark:text-slate-600">|</span>
                    <div class="flex items-center gap-1.5" title="Flashcard Dikuasai">
                        <i data-lucide="layers" class="w-4 h-4 text-amber-500"></i>
                        <span class="text-slate-500 dark:text-slate-400">Hafal:</span>
                        <span id="stat-fc-top" class="font-bold text-slate-800 dark:text-white">0</span>
                    </div>
                    <span class="text-slate-300 dark:text-slate-600">|</span>
                    <div class="flex items-center gap-1.5" title="Skor Kuis Tertinggi">
                        <i data-lucide="trophy" class="w-4 h-4 text-indigo-500"></i>
                        <span class="text-slate-500 dark:text-slate-400">Skor Kuis:</span>
                        <span id="stat-quiz-top" class="font-bold text-slate-800 dark:text-white">-</span>
                    </div>
                </div>

                <button id="theme-toggle" class="p-2.5 rounded-xl bg-slate-100 dark:bg-slate-800 text-slate-700 dark:text-amber-400 hover:bg-slate-200 dark:hover:bg-slate-700 transition" title="Ganti Mode Gelap/Terang">
                    <i data-lucide="moon" id="theme-icon-dark" class="w-5 h-5 block dark:hidden"></i>
                    <i data-lucide="sun" id="theme-icon-light" class="w-5 h-5 hidden dark:block"></i>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Layout Container -->
    <div class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 flex flex-col lg:flex-row gap-6">
        
        <!-- Sidebar Navigation (Desktop & Mobile Drawer) -->
        <aside id="sidebar" class="fixed inset-y-0 left-0 z-50 w-72 bg-white dark:bg-slate-900 border-r border-slate-200 dark:border-slate-800 p-5 transform -translate-x-full lg:translate-x-0 lg:static lg:w-64 lg:rounded-2xl lg:border lg:shadow-sm lg:h-fit lg:sticky lg:top-22 transition-transform duration-300 flex flex-col justify-between">
            <div>
                <div class="flex items-center justify-between lg:hidden mb-6 pb-4 border-b border-slate-200 dark:border-slate-800">
                    <span class="font-display font-bold text-sman4-800 dark:text-white">Menu Navigasi</span>
                    <button id="close-sidebar-btn" class="p-1.5 rounded-lg text-slate-500 hover:bg-slate-100 dark:hover:bg-slate-800">
                        <i data-lucide="x" class="w-5 h-5"></i>
                    </button>
                </div>

                <p class="text-xs font-bold uppercase tracking-wider text-slate-400 dark:text-slate-500 mb-3 px-3">Menu Utama</p>
                <nav class="space-y-1.5" id="main-nav">
                    <button data-tab="study-hub" class="nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold transition-all bg-sman4-800 text-white shadow-md shadow-sman4-800/20">
                        <i data-lucide="book-open" class="w-5 h-5 shrink-0"></i>
                        <span>Ringkasan Materi</span>
                    </button>
                    <button data-tab="text-bank" class="nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all">
                        <i data-lucide="file-text" class="w-5 h-5 shrink-0"></i>
                        <span>Bank Contoh Teks</span>
                    </button>
                    <button data-tab="quiz-arena" class="nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all">
                        <i data-lucide="check-circle-2" class="w-5 h-5 shrink-0"></i>
                        <span>Latihan Soal Kustom</span>
                    </button>
                    <button data-tab="active-recall" class="nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all">
                        <i data-lucide="brain-circuit" class="w-5 h-5 shrink-0"></i>
                        <span>Flashcard & Active Recall</span>
                    </button>
                    <button data-tab="ai-tutor" class="nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all">
                        <i data-lucide="sparkles" class="w-5 h-5 shrink-0 text-amber-500"></i>
                        <span>Tanya AI Tutor</span>
                    </button>
                </nav>
            </div>

            <!-- Progress Card in Sidebar -->
            <div class="mt-8 pt-5 border-t border-slate-200 dark:border-slate-800">
                <div class="bg-gradient-to-br from-sman4-800 via-indigo-900 to-slate-900 rounded-2xl p-4 text-white shadow-lg relative overflow-hidden">
                    <div class="absolute -right-4 -top-4 w-20 h-20 bg-emas-400/20 rounded-full blur-xl"></div>
                    <div class="flex items-center gap-2 mb-2">
                        <span class="w-2 h-2 rounded-full bg-emas-400 animate-pulse"></span>
                        <span class="text-xs font-bold text-emas-400 uppercase tracking-wider">Target Ulangan</span>
                    </div>
                    <h4 class="font-display font-bold text-sm mb-1">Kesiapan Ujianmu</h4>
                    <p class="text-xs text-indigo-200 mb-3">Tandai materi yang sudah dipahami & kuasai flashcard.</p>
                    
                    <div class="w-full bg-white/15 rounded-full h-2 mb-1.5">
                        <div id="overall-progress-bar" class="bg-emas-400 h-2 rounded-full transition-all duration-500" style="width: 10%"></div>
                    </div>
                    <div class="flex justify-between text-[11px] text-indigo-200">
                        <span id="overall-progress-text">10% Siap</span>
                        <button onclick="resetAllProgress()" class="underline hover:text-white">Reset</button>
                    </div>
                </div>
            </div>
        </aside>

        <!-- Mobile Backdrop -->
        <div id="sidebar-backdrop" class="fixed inset-0 bg-slate-900/50 backdrop-blur-xs z-40 hidden lg:hidden"></div>

        <!-- Main Content Area -->
        <main class="flex-1 min-w-0 space-y-6">
            
            <!-- Welcome Hero Banner -->
            <section class="bg-gradient-to-r from-sman4-800 via-indigo-800 to-blue-800 rounded-2xl p-6 sm:p-8 text-white shadow-lg relative overflow-hidden">
                <div class="absolute right-0 top-0 bottom-0 w-1/3 bg-gradient-to-l from-emas-400/15 to-transparent pointer-events-none"></div>
                <div class="relative z-10 flex flex-col md:flex-row md:items-center justify-between gap-6">
                    <div class="space-y-2 max-w-2xl">
                        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/10 backdrop-blur-xs border border-white/15 text-xs font-semibold text-emas-400">
                            <i data-lucide="award" class="w-3.5 h-3.5"></i>
                            <span>Semangat Ulangan Siswa-Siswi SMAN 4 Kendari!</span>
                        </div>
                        <h1 class="font-display text-2xl sm:text-3xl font-extrabold tracking-tight leading-tight">
                            Kuasai Materi Bahasa Indonesia Kelas X
                        </h1>
                        <p class="text-sm sm:text-base text-blue-100 leading-relaxed">
                            Pelajari struktur & kaidah Teks LHO, Eksposisi, Anekdot, hingga Hikayat berbasis STEM. Uji pemahamanmu lewat latihan soal kustom, flashcard, dan AI Tutor.
                        </p>
                    </div>
                    <!-- Mobile Quick Stats Grid -->
                    <div class="grid grid-cols-3 md:grid-cols-1 gap-2.5 shrink-0 bg-white/10 backdrop-blur-md p-3.5 rounded-xl border border-white/15">
                        <div class="text-center md:text-left flex flex-col md:flex-row md:items-center md:justify-between gap-1 md:gap-4">
                            <span class="text-xs text-blue-200">Materi Selesai</span>
                            <span id="hero-stat-materi" class="font-display font-bold text-base sm:text-lg text-emas-400">0 / 4</span>
                        </div>
                        <div class="text-center md:text-left flex flex-col md:flex-row md:items-center md:justify-between gap-1 md:gap-4 border-x md:border-x-0 md:border-y border-white/15 px-2 md:px-0 md:py-1.5">
                            <span class="text-xs text-blue-200">Kartu Hafal</span>
                            <span id="hero-stat-fc" class="font-display font-bold text-base sm:text-lg text-white">0 / 16</span>
                        </div>
                        <div class="text-center md:text-left flex flex-col md:flex-row md:items-center md:justify-between gap-1 md:gap-4">
                            <span class="text-xs text-blue-200">Skor Terbaik</span>
                            <span id="hero-stat-quiz" class="font-display font-bold text-base sm:text-lg text-emerald-300">-</span>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ========================================== -->
            <!-- TAB 1: RINGKASAN MATERI (STUDY HUB)        -->
            <!-- ========================================== -->
            <div id="tab-study-hub" class="tab-content fade-in space-y-6">
                <!-- Topic Selector Pills -->
                <div class="bg-white dark:bg-slate-900 p-2 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs flex flex-wrap gap-2">
                    <button onclick="selectTopic('lho')" id="topic-btn-lho" class="topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all bg-sman4-800 text-white shadow-xs flex items-center justify-center gap-2">
                        <i data-lucide="search-check" class="w-4 h-4"></i>
                        <span>1. Teks LHO</span>
                    </button>
                    <button onclick="selectTopic('eksposisi')" id="topic-btn-eksposisi" class="topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 flex items-center justify-center gap-2">
                        <i data-lucide="scale" class="w-4 h-4"></i>
                        <span>2. Teks Eksposisi</span>
                    </button>
                    <button onclick="selectTopic('anekdot')" id="topic-btn-anekdot" class="topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 flex items-center justify-center gap-2">
                        <i data-lucide="smile-plus" class="w-4 h-4"></i>
                        <span>3. Teks Anekdot</span>
                    </button>
                    <button onclick="selectTopic('hikayat')" id="topic-btn-hikayat" class="topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 flex items-center justify-center gap-2">
                        <i data-lucide="scroll-text" class="w-4 h-4"></i>
                        <span>4. Teks Hikayat & STEM</span>
                    </button>
                </div>

                <!-- Dynamic Topic Detail Container -->
                <div id="topic-detail-container" class="space-y-6"></div>
            </div>

            <!-- ========================================== -->
            <!-- TAB 2: BANK CONTOH TEKS LENGKAP            -->
            <!-- ========================================== -->
            <div id="tab-text-bank" class="tab-content hidden fade-in space-y-6">
                <div class="bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs">
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-6">
                        <div>
                            <h2 class="font-display text-xl font-bold text-slate-900 dark:text-white flex items-center gap-2">
                                <i data-lucide="library" class="w-6 h-6 text-sman4-600 dark:text-emas-400"></i>
                                <span>Bank Contoh Teks & Bedah Struktur</span>
                            </h2>
                            <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">Pilih jenis teks di bawah ini, baca teks lengkapnya, lalu klik tombol <strong>Bedah Analisis</strong> untuk melihat struktur dan kaidahnya.</p>
                        </div>
                        <!-- Filter Buttons -->
                        <div class="flex flex-wrap gap-2" id="text-filter-group">
                            <button onclick="filterTexts('all')" data-filter="all" class="text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-sman4-800 text-white">Semua (8)</button>
                            <button onclick="filterTexts('lho')" data-filter="lho" class="text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Teks LHO</button>
                            <button onclick="filterTexts('eksposisi')" data-filter="eksposisi" class="text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Eksposisi</button>
                            <button onclick="filterTexts('anekdot')" data-filter="anekdot" class="text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Anekdot</button>
                            <button onclick="filterTexts('hikayat')" data-filter="hikayat" class="text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Hikayat & STEM</button>
                        </div>
                    </div>

                    <!-- Texts List -->
                    <div id="texts-list-container" class="space-y-6"></div>
                </div>
            </div>

            <!-- ========================================== -->
            <!-- TAB 3: LATIHAN SOAL KUSTOM (QUIZ)          -->
            <!-- ========================================== -->
            <div id="tab-quiz-arena" class="tab-content hidden fade-in space-y-6">
                <!-- Quiz Setup Screen -->
                <div id="quiz-setup-screen" class="bg-white dark:bg-slate-900 p-6 sm:p-8 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs max-w-3xl mx-auto">
                    <div class="text-center max-w-xl mx-auto mb-8">
                        <div class="w-14 h-14 rounded-2xl bg-indigo-100 dark:bg-indigo-900/50 text-sman4-800 dark:text-emas-400 flex items-center justify-center mx-auto mb-4">
                            <i data-lucide="file-question" class="w-8 h-8"></i>
                        </div>
                        <h2 class="font-display text-2xl font-bold text-slate-900 dark:text-white">Simulasi Ulangan B.Indonesia</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">Atur topik materi dan jumlah soal yang ingin kamu kerjakan. Setiap soal dilengkapi pembahasan lengkap!</p>
                    </div>

                    <div class="space-y-6">
                        <!-- Pilih Materi -->
                        <div>
                            <label class="block text-sm font-bold text-slate-700 dark:text-slate-200 mb-3">1. Pilih Cakupan Materi</label>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3" id="quiz-topic-options">
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-topic" value="all" checked class="peer sr-only">
                                    <div class="p-4 rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-50/70 dark:peer-checked:bg-indigo-950/40 transition flex items-center gap-3">
                                        <i data-lucide="layers" class="w-5 h-5 text-sman4-600 dark:text-emas-400"></i>
                                        <div>
                                            <div class="font-bold text-sm">Semua Materi (Campuran)</div>
                                            <div class="text-xs text-slate-500">Simulasi ulangan lengkap</div>
                                        </div>
                                    </div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-topic" value="lho" class="peer sr-only">
                                    <div class="p-4 rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-50/70 dark:peer-checked:bg-indigo-950/40 transition flex items-center gap-3">
                                        <i data-lucide="search-check" class="w-5 h-5 text-emerald-500"></i>
                                        <div>
                                            <div class="font-bold text-sm">Teks LHO & Data Deskripsi</div>
                                            <div class="text-xs text-slate-500">Struktur, kaidah, olah data</div>
                                        </div>
                                    </div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-topic" value="eksposisi" class="peer sr-only">
                                    <div class="p-4 rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-50/70 dark:peer-checked:bg-indigo-950/40 transition flex items-center gap-3">
                                        <i data-lucide="scale" class="w-5 h-5 text-blue-500"></i>
                                        <div>
                                            <div class="font-bold text-sm">Teks Eksposisi</div>
                                            <div class="text-xs text-slate-500">Tesis, argumen, penegasan</div>
                                        </div>
                                    </div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-topic" value="anekdot" class="peer sr-only">
                                    <div class="p-4 rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-50/70 dark:peer-checked:bg-indigo-950/40 transition flex items-center gap-3">
                                        <i data-lucide="smile-plus" class="w-5 h-5 text-amber-500"></i>
                                        <div>
                                            <div class="font-bold text-sm">Teks Anekdot</div>
                                            <div class="text-xs text-slate-500">Krisis, reaksi, sindiran</div>
                                        </div>
                                    </div>
                                </label>
                                <label class="cursor-pointer sm:col-span-2">
                                    <input type="radio" name="quiz-topic" value="hikayat" class="peer sr-only">
                                    <div class="p-4 rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-50/70 dark:peer-checked:bg-indigo-950/40 transition flex items-center gap-3">
                                        <i data-lucide="scroll-text" class="w-5 h-5 text-purple-500"></i>
                                        <div>
                                            <div class="font-bold text-sm">Teks Hikayat (Ciri, Nilai & Integrasi STEM)</div>
                                            <div class="text-xs text-slate-500">Unsur intrinsik, nilai budaya/moral, analisis sains</div>
                                        </div>
                                    </div>
                                </label>
                            </div>
                        </div>

                        <!-- Pilih Jumlah Soal -->
                        <div>
                            <label class="block text-sm font-bold text-slate-700 dark:text-slate-200 mb-3">2. Pilih Jumlah Soal</label>
                            <div class="grid grid-cols-4 gap-3">
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-count" value="5" checked class="peer sr-only">
                                    <div class="py-3 text-center rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-800 peer-checked:text-white font-bold text-sm transition">5 Soal</div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-count" value="10" class="peer sr-only">
                                    <div class="py-3 text-center rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-800 peer-checked:text-white font-bold text-sm transition">10 Soal</div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-count" value="15" class="peer sr-only">
                                    <div class="py-3 text-center rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-800 peer-checked:text-white font-bold text-sm transition">15 Soal</div>
                                </label>
                                <label class="cursor-pointer">
                                    <input type="radio" name="quiz-count" value="20" class="peer sr-only">
                                    <div class="py-3 text-center rounded-xl border-2 border-slate-200 dark:border-slate-700 peer-checked:border-sman4-600 peer-checked:bg-sman4-800 peer-checked:text-white font-bold text-sm transition">20 Soal</div>
                                </label>
                            </div>
                        </div>

                        <!-- Timer Option -->
                        <div class="flex items-center justify-between p-4 rounded-xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200 dark:border-slate-700">
                            <div class="flex items-center gap-3">
                                <i data-lucide="timer" class="w-5 h-5 text-amber-500"></i>
                                <div>
                                    <div class="text-sm font-bold">Mode Timer Ujian</div>
                                    <div class="text-xs text-slate-500">1 menit per soal untuk melatih manajemen waktu</div>
                                </div>
                            </div>
                            <input type="checkbox" id="quiz-timer-toggle" class="w-5 h-5 accent-sman4-800 rounded cursor-pointer">
                        </div>

                        <button onclick="startQuiz()" class="w-full py-4 rounded-xl bg-gradient-to-r from-sman4-800 to-indigo-700 hover:from-sman4-700 hover:to-indigo-600 text-white font-display font-bold text-base shadow-lg shadow-sman4-800/25 transition flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-5 h-5"></i>
                            <span>Mulai Kerjakan Latihan Soal</span>
                        </button>
                    </div>
                </div>

                <!-- Active Quiz Screen -->
                <div id="quiz-active-screen" class="hidden bg-white dark:bg-slate-900 p-6 sm:p-8 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs max-w-3xl mx-auto">
                    <div class="flex items-center justify-between gap-4 pb-4 mb-6 border-b border-slate-200 dark:border-slate-800">
                        <div class="flex items-center gap-3">
                            <span id="quiz-progress-badge" class="px-3 py-1 rounded-lg bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-indigo-300 font-bold text-xs">Soal 1 / 5</span>
                            <span id="quiz-category-badge" class="px-3 py-1 rounded-lg bg-amber-100 dark:bg-amber-950/60 text-amber-800 dark:text-amber-300 font-semibold text-xs">Teks LHO</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <div id="quiz-timer-display" class="hidden items-center gap-1.5 px-3 py-1 rounded-lg bg-rose-100 dark:bg-rose-950 text-rose-700 dark:text-rose-300 font-mono font-bold text-sm">
                                <i data-lucide="clock" class="w-4 h-4"></i>
                                <span id="quiz-timer-text">05:00</span>
                            </div>
                            <button onclick="quitQuiz()" class="text-xs font-semibold text-slate-400 hover:text-rose-500">Keluar</button>
                        </div>
                    </div>

                    <!-- Progress Bar -->
                    <div class="w-full bg-slate-100 dark:bg-slate-800 h-2 rounded-full mb-6">
                        <div id="quiz-bar" class="bg-sman4-600 h-2 rounded-full transition-all duration-300" style="width: 20%"></div>
                    </div>

                    <!-- Question Passage (if any) & Question Text -->
                    <div id="quiz-passage" class="hidden mb-5 p-4 rounded-xl bg-slate-50 dark:bg-slate-800/80 border-l-4 border-sman4-600 text-sm leading-relaxed text-slate-700 dark:text-slate-300"></div>
                    <h3 id="quiz-question-text" class="font-display font-bold text-lg text-slate-900 dark:text-white mb-5 leading-snug"></h3>

                    <!-- Options -->
                    <div id="quiz-options-container" class="space-y-3 mb-6"></div>

                    <!-- Navigation Buttons -->
                    <div class="flex items-center justify-between pt-4 border-t border-slate-200 dark:border-slate-800">
                        <button id="quiz-prev-btn" onclick="prevQuestion()" class="px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 text-sm font-semibold hover:bg-slate-100 dark:hover:bg-slate-800 disabled:opacity-40">Sebelumnya</button>
                        <button id="quiz-next-btn" onclick="nextQuestion()" class="px-6 py-2.5 rounded-xl bg-sman4-800 hover:bg-sman4-700 text-white text-sm font-bold shadow-sm">Selanjutnya</button>
                    </div>
                </div>

                <!-- Quiz Result & Pembahasan Screen -->
                <div id="quiz-result-screen" class="hidden space-y-6 max-w-3xl mx-auto">
                    <div class="bg-white dark:bg-slate-900 p-6 sm:p-8 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs text-center">
                        <div class="w-16 h-16 rounded-full bg-emas-400/20 text-emas-500 flex items-center justify-center mx-auto mb-4">
                            <i data-lucide="trophy" class="w-9 h-9"></i>
                        </div>
                        <h2 class="font-display text-2xl font-extrabold text-slate-900 dark:text-white">Hasil Latihan Soalmu</h2>
                        <p id="quiz-result-subtitle" class="text-sm text-slate-500 dark:text-slate-400 mt-1">Kerja bagus! Terus tingkatkan pemahamanmu.</p>
                        
                        <div class="my-6 inline-flex items-baseline gap-1 bg-slate-50 dark:bg-slate-800 px-8 py-4 rounded-2xl border border-slate-200 dark:border-slate-700">
                            <span id="quiz-final-score" class="font-display text-5xl font-extrabold text-sman4-800 dark:text-emas-400">80</span>
                            <span class="text-slate-400 font-bold">/ 100</span>
                        </div>

                        <div class="grid grid-cols-3 gap-3 max-w-md mx-auto mb-6 text-sm">
                            <div class="p-3 rounded-xl bg-emerald-50 dark:bg-emerald-950/40 text-emerald-700 dark:text-emerald-300">
                                <div class="font-bold text-lg" id="quiz-correct-count">4</div>
                                <div class="text-xs">Benar</div>
                            </div>
                            <div class="p-3 rounded-xl bg-rose-50 dark:bg-rose-950/40 text-rose-700 dark:text-rose-300">
                                <div class="font-bold text-lg" id="quiz-wrong-count">1</div>
                                <div class="text-xs">Salah</div>
                            </div>
                            <div class="p-3 rounded-xl bg-blue-50 dark:bg-blue-950/40 text-blue-700 dark:text-blue-300">
                                <div class="font-bold text-lg" id="quiz-total-count">5</div>
                                <div class="text-xs">Total Soal</div>
                            </div>
                        </div>

                        <button onclick="resetQuizUI()" class="px-6 py-3 rounded-xl bg-sman4-800 hover:bg-sman4-700 text-white font-bold text-sm shadow-md">
                            Buat Latihan Baru
                        </button>
                    </div>

                    <!-- Detailed Explanations -->
                    <div class="bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs">
                        <h3 class="font-display font-bold text-lg mb-4 flex items-center gap-2">
                            <i data-lucide="list-checks" class="w-5 h-5 text-sman4-600"></i>
                            <span>Pembahasan Detail Setiap Nomor</span>
                        </h3>
                        <div id="quiz-review-list" class="space-y-4"></div>
                    </div>
                </div>
            </div>

            <!-- ========================================== -->
            <!-- TAB 4: FLASHCARD & ACTIVE RECALL           -->
            <!-- ========================================== -->
            <div id="tab-active-recall" class="tab-content hidden fade-in space-y-6">
                <!-- Sub-mode Switcher -->
                <div class="bg-white dark:bg-slate-900 p-4 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                    <div class="flex gap-2">
                        <button onclick="switchRecallMode('flashcard')" id="btn-mode-fc" class="px-4 py-2.5 rounded-xl text-sm font-bold bg-sman4-800 text-white flex items-center gap-2">
                            <i data-lucide="layers" class="w-4 h-4"></i>
                            <span>Flashcard 3D</span>
                        </button>
                        <button onclick="switchRecallMode('recall')" id="btn-mode-ar" class="px-4 py-2.5 rounded-xl text-sm font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 flex items-center gap-2">
                            <i data-lucide="brain" class="w-4 h-4"></i>
                            <span>Uji Ingatan Aktif</span>
                        </button>
                    </div>

                    <!-- Topic Filter for Recall -->
                    <select id="recall-topic-filter" onchange="filterRecallItems()" class="px-3.5 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm font-semibold focus:outline-none">
                        <option value="all">Semua Materi (16 Kartu)</option>
                        <option value="lho">Teks LHO</option>
                        <option value="eksposisi">Teks Eksposisi</option>
                        <option value="anekdot">Teks Anekdot</option>
                        <option value="hikayat">Teks Hikayat & STEM</option>
                    </select>
                </div>

                <!-- MODE A: FLASHCARD 3D -->
                <div id="recall-flashcard-view" class="max-w-2xl mx-auto space-y-5">
                    <div class="flex items-center justify-between text-xs font-bold text-slate-500 dark:text-slate-400 px-1">
                        <span id="fc-counter">Kartu 1 dari 16</span>
                        <span id="fc-status-badge" class="px-2.5 py-1 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300">Belum Hafal</span>
                    </div>

                    <!-- 3D Flip Card -->
                    <div class="perspective-1000 h-72 sm:h-80 cursor-pointer" onclick="flipFlashcard()">
                        <div id="flashcard-inner" class="relative w-full h-full transform-style-3d">
                            <!-- Front -->
                            <div class="absolute inset-0 backface-hidden bg-white dark:bg-slate-900 rounded-3xl border-2 border-slate-200 dark:border-slate-800 shadow-md p-6 sm:p-8 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span id="fc-front-tag" class="px-3 py-1 rounded-full bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-indigo-300 text-xs font-bold">TEKS LHO</span>
                                    <span class="text-xs text-slate-400 flex items-center gap-1"><i data-lucide="rotate-cw" class="w-3.5 h-3.5"></i> Klik kartu untuk balik</span>
                                </div>
                                <div class="text-center my-auto">
                                    <h3 id="fc-front-text" class="font-display text-xl sm:text-2xl font-bold text-slate-900 dark:text-white leading-snug"></h3>
                                </div>
                                <div class="text-center text-xs text-slate-400">Uji ingatanmu sebelum membuka jawaban</div>
                            </div>

                            <!-- Back -->
                            <div class="absolute inset-0 backface-hidden rotate-y-180 bg-gradient-to-br from-sman4-800 to-indigo-900 text-white rounded-3xl shadow-lg p-6 sm:p-8 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="px-3 py-1 rounded-full bg-emas-400/20 text-emas-400 text-xs font-bold">JAWABAN & KONSEP</span>
                                    <span class="text-xs text-indigo-200 flex items-center gap-1"><i data-lucide="rotate-cw" class="w-3.5 h-3.5"></i> Klik untuk kembali</span>
                                </div>
                                <div class="my-auto overflow-y-auto max-h-48 pr-1">
                                    <p id="fc-back-text" class="text-sm sm:text-base leading-relaxed text-indigo-50"></p>
                                </div>
                                <div class="text-center text-xs text-indigo-300">Tandai penguasaanmu di tombol bawah</div>
                            </div>
                        </div>
                    </div>

                    <!-- Flashcard Controls -->
                    <div class="flex flex-wrap items-center justify-between gap-3">
                        <div class="flex gap-2">
                            <button onclick="prevFlashcard()" class="p-3 rounded-xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 hover:bg-slate-100 dark:hover:bg-slate-800">
                                <i data-lucide="chevron-left" class="w-5 h-5"></i>
                            </button>
                            <button onclick="nextFlashcard()" class="p-3 rounded-xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 hover:bg-slate-100 dark:hover:bg-slate-800">
                                <i data-lucide="chevron-right" class="w-5 h-5"></i>
                            </button>
                        </div>

                        <div class="flex gap-2 flex-1 sm:flex-initial justify-end">
                            <button onclick="markFlashcard(false)" class="px-4 py-3 rounded-xl bg-amber-100 dark:bg-amber-950/60 text-amber-800 dark:text-amber-300 font-bold text-xs sm:text-sm hover:bg-amber-200 transition flex items-center gap-1.5">
                                <i data-lucide="refresh-ccw" class="w-4 h-4"></i>
                                <span>Ulangi Lagi</span>
                            </button>
                            <button onclick="markFlashcard(true)" class="px-4 py-3 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs sm:text-sm shadow-sm transition flex items-center gap-1.5">
                                <i data-lucide="check" class="w-4 h-4"></i>
                                <span>Sudah Hafal</span>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- MODE B: ACTIVE RECALL (TYPED SELF-TEST) -->
                <div id="recall-active-view" class="hidden max-w-2xl mx-auto bg-white dark:bg-slate-900 p-6 sm:p-8 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs space-y-5">
                    <div class="flex items-center justify-between">
                        <span id="ar-tag" class="px-3 py-1 rounded-full bg-purple-100 dark:bg-purple-950 text-purple-800 dark:text-purple-300 text-xs font-bold">ACTIVE RECALL</span>
                        <span id="ar-counter" class="text-xs font-bold text-slate-400">Pertanyaan 1 / 12</span>
                    </div>

                    <div>
                        <h3 id="ar-prompt" class="font-display text-lg sm:text-xl font-bold text-slate-900 dark:text-white leading-snug"></h3>
                        <p class="text-xs text-slate-500 mt-1">Tuliskan poin-poin jawaban dari ingatanmu sendiri sebelum membuka kunci jawaban.</p>
                    </div>

                    <textarea id="ar-user-input" rows="4" placeholder="Ketik jawabanmu di sini..." class="w-full p-4 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm focus:ring-2 focus:ring-sman4-600 focus:outline-none"></textarea>

                    <div id="ar-answer-box" class="hidden p-4 rounded-xl bg-emerald-50 dark:bg-emerald-950/40 border border-emerald-200 dark:border-emerald-800/60 space-y-2 fade-in">
                        <div class="text-xs font-bold text-emerald-700 dark:text-emerald-400 uppercase tracking-wider">Kunci Jawaban & Poin Penting:</div>
                        <p id="ar-ideal-answer" class="text-sm text-slate-800 dark:text-slate-200 leading-relaxed"></p>
                    </div>

                    <div class="flex flex-wrap items-center justify-between gap-3 pt-2">
                        <button onclick="revealActiveRecall()" id="ar-reveal-btn" class="px-5 py-2.5 rounded-xl bg-sman4-800 hover:bg-sman4-700 text-white font-bold text-sm flex items-center gap-2">
                            <i data-lucide="eye" class="w-4 h-4"></i>
                            <span>Buka Kunci Jawaban & Evaluasi</span>
                        </button>
                        <div class="flex gap-2">
                            <button onclick="nextActiveRecall()" class="px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 text-sm font-semibold hover:bg-slate-100 dark:hover:bg-slate-800 flex items-center gap-1">
                                <span>Soal Berikutnya</span>
                                <i data-lucide="arrow-right" class="w-4 h-4"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ========================================== -->
            <!-- TAB 5: TANYA AI TUTOR B.INDO               -->
            <!-- ========================================== -->
            <div id="tab-ai-tutor" class="tab-content hidden fade-in">
                <div class="bg-white dark:bg-slate-900 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs overflow-hidden flex flex-col h-[620px]">
                    <!-- Chat Header -->
                    <div class="p-4 sm:p-5 bg-gradient-to-r from-sman4-800 to-indigo-800 text-white flex items-center justify-between">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-xl bg-emas-400/20 border border-emas-400/40 flex items-center justify-center text-emas-400">
                                <i data-lucide="bot" class="w-6 h-6"></i>
                            </div>
                            <div>
                                <h3 class="font-display font-bold text-base">Kak AI Tutor B.Indonesia</h3>
                                <p class="text-xs text-blue-200">Siap bantu jelasin materi kelas X SMAN 4 Kendari!</p>
                            </div>
                        </div>
                        <button onclick="clearChat()" class="text-xs bg-white/10 hover:bg-white/20 px-3 py-1.5 rounded-lg transition">Reset Chat</button>
                    </div>

                    <!-- Quick Prompt Suggestions -->
                    <div class="p-3 bg-slate-50 dark:bg-slate-800/60 border-b border-slate-200 dark:border-slate-800 flex gap-2 overflow-x-auto">
                        <button onclick="sendQuickPrompt('Jelaskan perbedaan kalimat definisi dan kalimat deskripsi di teks LHO beserta contohnya!')" class="shrink-0 text-xs px-3 py-1.5 rounded-full bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 hover:border-sman4-600 transition font-medium">
                            Bedakan definisi & deskripsi LHO
                        </button>
                        <button onclick="sendQuickPrompt('Bagaimana cara cepat menentukan Tesis, Argumentasi, dan Penegasan Ulang pada Teks Eksposisi saat ulangan?')" class="shrink-0 text-xs px-3 py-1.5 rounded-full bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 hover:border-sman4-600 transition font-medium">
                            Trik identifikasi struktur Eksposisi
                        </button>
                        <button onclick="sendQuickPrompt('Apa hubungan nilai dan unsur Teks Hikayat dengan pembelajaran STEM (Sains, Teknologi, Rekayasa, Matematika)?')" class="shrink-0 text-xs px-3 py-1.5 rounded-full bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 hover:border-sman4-600 transition font-medium">
                            Hikayat dalam pembelajaran STEM
                        </button>
                        <button onclick="sendQuickPrompt('Buatkan contoh paragraf deskripsi LHO tentang Teluk Kendari atau Hutan Mangrove!')" class="shrink-0 text-xs px-3 py-1.5 rounded-full bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 hover:border-sman4-600 transition font-medium">
                            Contoh deskripsi LHO Kendari
                        </button>
                    </div>

                    <!-- Chat Messages Area -->
                    <div id="chat-messages" class="flex-1 p-4 sm:p-6 overflow-y-auto space-y-4">
                        <div class="flex gap-3 max-w-2xl">
                            <div class="w-8 h-8 rounded-lg bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-emas-400 flex items-center justify-center shrink-0 mt-1">
                                <i data-lucide="sparkles" class="w-4 h-4"></i>
                            </div>
                            <div class="bg-slate-100 dark:bg-slate-800 p-4 rounded-2xl rounded-tl-none text-sm leading-relaxed text-slate-800 dark:text-slate-200">
                                Halo siswa-siswi hebat <strong>SMAN 4 Kendari</strong>! 👋<br><br>
                                Ada materi Bahasa Indonesia Kelas X yang bikin bingung menjelang ulangan? Kamu bisa tanya apa saja seputar:
                                <ul class="list-disc ml-5 mt-1 space-y-0.5">
                                    <li>Struktur & kaidah <strong>Teks LHO</strong> serta cara mengolah data menjadi paragraf deskripsi</li>
                                    <li>Cara membedah tesis & argumen <strong>Teks Eksposisi</strong></li>
                                    <li>Struktur krisis & sindiran <strong>Teks Anekdot</strong></li>
                                    <li>Ciri, nilai, dan penerapan <strong>Teks Hikayat dalam STEM</strong></li>
                                </ul>
                                Ketik pertanyaanmu di bawah ya!
                            </div>
                        </div>
                    </div>

                    <!-- Chat Input Form -->
                    <form id="chat-form" onsubmit="handleChatSubmit(event)" class="p-4 bg-white dark:bg-slate-900 border-t border-slate-200 dark:border-slate-800 flex gap-2">
                        <input type="text" id="chat-input" required placeholder="Tanya materi B.Indonesia di sini (misal: Apa itu alur berbingkai pada hikayat?)..." class="flex-1 px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm focus:ring-2 focus:ring-sman4-600 focus:outline-none">
                        <button type="submit" id="chat-send-btn" class="px-5 py-3 rounded-xl bg-sman4-800 hover:bg-sman4-700 text-white font-bold text-sm flex items-center gap-2 transition shrink-0">
                            <span>Kirim</span>
                            <i data-lucide="send" class="w-4 h-4"></i>
                        </button>
                    </form>
                </div>
            </div>

        </main>
    </div>

    <!-- Footer -->
    <footer class="mt-auto border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900 py-5 px-4 text-center text-xs text-slate-500 dark:text-slate-400">
        <p>Dashboard Persiapan Ulangan Bahasa Indonesia Kelas X &bull; Dirancang khusus untuk Pelajar <strong>SMAN 4 Kendari</strong></p>
    </footer>

    <!-- ========================================== -->
    <!-- JAVASCRIPT APPLICATION LOGIC & DATA        -->
    <!-- ========================================== -->
    <script>
        // ==========================================
        // 1. RICH CURRICULUM DATA (MATERI LENGKAP)
        // ==========================================
        const CURRICULUM_DATA = {
            lho: {
                id: 'lho',
                title: 'Teks Laporan Hasil Observasi (LHO)',
                subtitle: 'Menyajikan fakta objektif hasil pengamatan langsung secara sistematis dan ilmiah.',
                badgeColor: 'emerald',
                structures: [
                    {
                        name: '1. Pernyataan Umum / Klasifikasi',
                        desc: 'Berisi pembuka atau informasi umum mengenai objek yang diamati, meliputi definisi, nama ilmiah/latin, dan klasifikasi umum.',
                        clue: 'Ciri khas: Menggunakan kalimat definisi (adalah, merupakan, yaitu, yakni).'
                    },
                    {
                        name: '2. Deskripsi Bagian',
                        desc: 'Berisi perincian bagian-bagian objek yang diamati secara mendetail (ciri fisik, ukuran, warna, habitat, perilaku, atau komponen).',
                        clue: 'Ciri khas: Menggunakan kalimat deskripsi yang merinci sifat/keadaan objek secara objektif.'
                    },
                    {
                        name: '3. Deskripsi Manfaat / Simpulan',
                        desc: 'Menjelaskan fungsi, kegunaan, atau dampak positif dari objek yang dilaporkan bagi manusia maupun lingkungan.',
                        clue: 'Ciri khas: Memuat kata bermanfaat, berfungsi, berguna, dimanfaatkan untuk...'
                    }
                ],
                kaidah: [
                    { title: 'Kata Benda (Nomina) & Frasa Nomina', detail: 'Menyebutkan objek yang diamati secara spesifik. Contoh: "terumbu karang", "ekosistem pesisir Teluk Kendari".' },
                    { title: 'Verba Relasional (Kata Kerja Penghubung)', detail: 'Digunakan untuk menyatakan definisi atau klasifikasi. Contoh: adalah, merupakan, termasuk, digolongkan, terdiri atas.' },
                    { title: 'Verba Aktif', detail: 'Menjelaskan perilaku atau aktivitas objek tanpa imbuhan pasif. Contoh: tumbuh, hidup, menyerap, menghasilkan.' },
                    { title: 'Kata Keilmuan / Istilah Teknis', detail: 'Kosakata khusus bidang keilmuan (biologi, geografi, dll.). Contoh: fotosintesis, abrasi, salinitas, Rhizophora.' },
                    { title: 'Kalimat Definisi vs Kalimat Deskripsi', detail: 'Definisi menjelaskan makna umum ("Mangrove adalah tumbuhan halofit..."). Deskripsi menggambarkan sifat fisik ("Akar tunjangnya menjulang setinggi 1-2 meter...").' }
                ],
                dataWorkshop: {
                    title: 'Latihan Menyusun Paragraf Deskripsi Sesuai Data LHO',
                    instruction: 'Perhatikan tabel hasil observasi tanaman Bakau (Rhizophora) di Pesisir Teluk Kendari berikut, lalu susun menjadi 1 paragraf deskripsi bagian yang padu dan objektif!',
                    tableHeaders: ['Aspek Pengamatan', 'Data Faktual Hasil Observasi'],
                    tableRows: [
                        ['Tinggi Pohon', 'Mencapai 5 hingga 15 meter pada usia dewasa'],
                        ['Bentuk Akar', 'Akar tunjang (stilt roots) bercabang banyak, mencengkeram lumpur pasang surut'],
                        ['Karakteristik Daun', 'Berbentuk elips, berwarna hijau mengilap, tebal, panjang 10–15 cm'],
                        ['Fungsi Fisik Akar', 'Meredam gelombang laut dan menahan sedimen lumpur agar tidak abrasi']
                    ],
                    idealAnswer: 'Tanaman bakau jenis Rhizophora yang tumbuh di pesisir Teluk Kendari memiliki tinggi batang mencapai 5 hingga 15 meter pada usia dewasa. Tumbuhan ini memiliki ciri khas berupa akar tunjang yang bercabang banyak dan mencengkeram kuat substrat lumpur di zona pasang surut. Daunnya berbentuk elips dengan permukaan hijau mengilap, bertekstur tebal, serta berukuran panjang sekitar 10 sampai 15 sentimeter. Susunan akar tunjangnya yang rapat berperan penting dalam meredam energi gelombang laut sekaligus menahan sedimen lumpur sehingga mencegah terjadinya abrasi pantai.'
                }
            },
            eksposisi: {
                id: 'eksposisi',
                title: 'Teks Eksposisi',
                subtitle: 'Memaparkan gagasan, pendapat, atau sudut pandang penulis yang diperkuat fakta dan argumen logis.',
                badgeColor: 'blue',
                structures: [
                    {
                        name: '1. Tesis (Pernyataan Pendapat)',
                        desc: 'Bagian pembuka yang berisi isu, permasalahan, serta pandangan/sikap awal penulis terhadap topik yang dibahas.',
                        clue: 'Cara identifikasi: Cari kalimat opini utama di paragraf pertama yang menjadi payung seluruh argumen.'
                    },
                    {
                        name: '2. Argumentasi',
                        desc: 'Berisi alasan-alasan logis, fakta lapangan, data statistik, atau kutipan pendapat ahli untuk membuktikan kebenaran tesis.',
                        clue: 'Cara identifikasi: Terdiri dari beberapa paragraf tengah yang memuat angka, hasil riset, atau hubungan sebab-akibat.'
                    },
                    {
                        name: '3. Penegasan Ulang (Reiterasi)',
                        desc: 'Bagian penutup yang merangkum kembali tesis dengan bahasa berbeda serta memberikan rekomendasi atau simpulan.',
                        clue: 'Cara identifikasi: Berada di paragraf akhir, sering diawali konjungsi penyimpul (oleh karena itu, dengan demikian).'
                    }
                ],
                kaidah: [
                    { title: 'Istilah Teknis / Keilmuan', detail: 'Istilah sesuai topik bahasan agar tulisan kredibel. Contoh: emisi karbon, literasi digital, inflasi, kurikulum.' },
                    { title: 'Konjungsi Kausalitas (Sebab-Akibat)', detail: 'Menghubungkan argumen dengan bukti. Contoh: sebab, karena, sehingga, akibatnya, oleh karena itu, berdampak pada.' },
                    { title: 'Kata Kerja Mental (Verba Mental)', detail: 'Menggambarkan respons batin atau pemikiran penulis/ahli. Contoh: berpendapat, menyimpulkan, memperkirakan, mengkritisi, meyakini.' },
                    { title: 'Kata Perujukan', detail: 'Merujuk pada sumber data/ahli untuk memperkuat argumen. Contoh: berdasarkan data..., menurut penelitian..., merujuk pada...' },
                    { title: 'Kata Persuasif', detail: 'Ajakan halus kepada pembaca agar sepakat dengan tesis. Contoh: hendaknya, sebaiknya, perlu, diharapkan, harus.' }
                ]
            },
            anekdot: {
                id: 'anekdot',
                title: 'Teks Anekdot',
                subtitle: 'Cerita singkat yang lucu dan mengesankan, bertujuan menyampaikan kritik sosial atau sindiran halus.',
                badgeColor: 'amber',
                structures: [
                    {
                        name: '1. Abstraksi',
                        desc: 'Gambaran awal mengenai isi cerita atau latar belakang peristiwa secara singkat (bersifat opsional).',
                        clue: 'Posisi: Kalimat pembuka paling awal.'
                    },
                    {
                        name: '2. Orientasi',
                        desc: 'Pengenalan tokoh, latar tempat, waktu, dan situasi awal sebelum munculnya masalah.',
                        clue: 'Posisi: Awal cerita setelah abstraksi.'
                    },
                    {
                        name: '3. Krisis',
                        desc: 'Puncak masalah atau bagian munculnya kekonyolan, kelucuan, sekaligus inti sindiran sosial.',
                        clue: 'Posisi: Bagian tengah yang memicu tawa atau rasa heran pembaca.'
                    },
                    {
                        name: '4. Reaksi',
                        desc: 'Tanggapan atau respons tokoh lain terhadap peristiwa konyol/sindiran pada bagian krisis.',
                        clue: 'Posisi: Tepat setelah krisis terjadi (bisa berupa keterkejutan, pembelaan diri, atau tawa).'
                    },
                    {
                        name: '5. Koda',
                        desc: 'Penutup cerita yang menandai berakhirnya peristiwa atau perubahan sikap tokoh (bersifat opsional).',
                        clue: 'Posisi: Akhir paragraf.'
                    }
                ],
                kaidah: [
                    { title: 'Kalimat Retoris', detail: 'Pertanyaan yang tidak memerlukan jawaban karena jawabannya sudah jelas atau untuk menyindir. Contoh: "Apakah uang rakyat bisa kenyang dimakan sendiri?"' },
                    { title: 'Konjungsi Waktu (Temporal)', detail: 'Menunjukkan urutan kejadian cerita. Contoh: kemudian, lalu, setelah itu, pada suatu hari, akhirnya.' },
                    { title: 'Kata Kerja Aksi (Verba Material)', detail: 'Menunjukkan tindakan nyata tokoh. Contoh: berjalan, mengetuk, menulis, tertawa, menyerahkan.' },
                    { title: 'Kalimat Seru & Perintah', detail: 'Menegaskan ekspresi emosi atau dialog antar tokoh. Contoh: "Wah, hebat sekali pelayanan kantor ini!"' },
                    { title: 'Majas Sindiran (Ironi, Sinisme, Sarkasme)', detail: 'Menyampaikan kritik secara tidak langsung melalui pujian terbalik atau perbandingan kontras.' }
                ]
            },
            hikayat: {
                id: 'hikayat',
                title: 'Teks Hikayat & Penerapan STEM',
                subtitle: 'Karya sastra Melayu klasik berbentuk prosa yang sarat nilai luhur dan dapat dikaji secara ilmiah (STEM).',
                badgeColor: 'purple',
                structures: [
                    {
                        name: 'Ciri-Ciri Khas Teks Hikayat',
                        desc: '1) Kemustahilan (hal tidak logis secara kasat mata), 2) Kesaktian tokoh, 3) Anonim (tanpa nama pengarang), 4) Istana sentris (berlatar kerajaan), 5) Alur berbingkai (cerita di dalam cerita), 6) Bahasa Melayu klasik/arkais (hatta, syahdan, alkisah).'
                    },
                    {
                        name: 'Unsur Intrinsik Hikayat',
                        desc: 'Meliputi Tema (gagasan pokok), Tokoh & Penokohan (protagonis/antagonis), Alur (maju/berbingkai), Latar (tempat, waktu, suasana istana/hutan), Sudut Pandang (orang ketiga serba tahu), Gaya Bahasa (majas hiperbola/simile), dan Amanat.'
                    },
                    {
                        name: 'Nilai-Nilai dalam Hikayat',
                        desc: '• Nilai Religi: ketakwaan dan doa kepada Tuhan.\n• Nilai Moral: kejujuran, budi pekerti, tanggung jawab.\n• Nilai Sosial: tolong-menolong, keadilan pemimpin.\n• Nilai Budaya: adat istiadat kerajaan, musyawarah.\n• Nilai Edukasi: pentingnya menuntut ilmu dan kecerdikan.'
                    },
                    {
                        name: 'Penerapan Hikayat dalam Pembelajaran STEM',
                        desc: '• Science (Sains): Menganalisis fenomena alam/biologi di balik kisah (misal: khasiat tanaman obat dalam hikayat secara fitokimia, atau hukum fisika pada benda terbang).\n• Technology (Teknologi): Merancang simulasi digital, gim edukasi, atau infografis interaktif dari alur hikayat.\n• Engineering (Rekayasa): Merekayasa alat pemecah masalah seperti yang dilakukan tokoh cerdik (misal: sistem katrol/jembatan).\n• Mathematics (Matematika): Menghitung logika pembagian harta, jarak perjalanan, atau pola kombinasi teka-teki dalam cerita.'
                    }
                ],
                kaidah: [
                    { title: 'Kata Arkais (Bahasa Melayu Klasik)', detail: 'Kosakata kuno yang jarang dipakai sekarang. Contoh: hatta (lalu), syahdan (selanjutnya), titah (perintah), upeti (pajak), mahligai (istana).' },
                    { title: 'Konjungsi Urutan Waktu', detail: 'Menghubungkan rangkaian peristiwa panjang. Contoh: maka, setelah itu, arakian, kalakian.' },
                    { title: 'Majas Hiperbola & Perbandingan', detail: 'Melebih-lebihkan kehebatan atau kecantikan tokoh. Contoh: "Wajahnya bersinar bagai bulan purnama empat belas hari."' }
                ]
            }
        };

        // ==========================================
        // 2. BANK CONTOH TEKS LENGKAP (8 TEKS)
        // ==========================================
        const SAMPLE_TEXTS = [
            {
                id: 'txt-lho-1',
                category: 'lho',
                categoryLabel: 'Teks LHO',
                title: 'Ekosistem Terumbu Karang di Pulau Bokori, Sulawesi Tenggara',
                segments: [
                    {
                        tag: 'Pernyataan Umum / Klasifikasi',
                        tagColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-950 dark:text-emerald-300',
                        text: 'Terumbu karang merupakan ekosistem bawah laut yang dibangun oleh penghasil kapur utama, yakni hewan karang batu (Scleractinia) yang bersimbiosis dengan alga mikroskopis Zooxanthellae. Di perairan sekitar Pulau Bokori, Sulawesi Tenggara, terumbu karang termasuk dalam tipe terumbu karang tepi (fringing reef) yang berkembang di perairan dangkal dan jernih.'
                    },
                    {
                        tag: 'Deskripsi Bagian',
                        tagColor: 'bg-blue-100 text-blue-800 dark:bg-blue-950 dark:text-blue-300',
                        text: 'Secara morfologis, koloni karang di kawasan ini memiliki bentuk pertumbuhan yang beragam, seperti karang bercabang (branching), karang massif menyerupai kubah batu, serta karang meja (tabular). Warna-warni cerah pada jaringan karang berasal dari pigmen alga Zooxanthellae yang hidup di dalam jaringan polip. Selain karang, ekosistem ini menjadi habitat bagi puluhan spesies ikan hias karang seperti ikan badut (Amphiprion) dan ikan kepe-kepe.'
                    },
                    {
                        tag: 'Deskripsi Manfaat',
                        tagColor: 'bg-amber-100 text-amber-800 dark:bg-amber-950 dark:text-amber-300',
                        text: 'Keberadaan terumbu karang memberikan manfaat ekologis dan ekonomis yang sangat besar. Secara ekologis, struktur kapurnya berfungsi sebagai pemecah gelombang alami yang melindungi garis pantai Pulau Bokori dari abrasi. Sementara secara ekonomis, kelestarian terumbu karang mendukung sektor ekowisata bahari dan menjadi daerah asuhan (nursery ground) bagi ikan-ikan konsumsi bernilai tinggi bagi nelayan lokal.'
                    }
                ],
                analysisNote: 'Kaidah Kebahasaan: Terdapat verba relasional ("merupakan", "termasuk"), istilah ilmiah ("Scleractinia", "fringing reef", "abrasi"), kalimat definisi pada paragraf 1, dan kalimat deskripsi rinci pada paragraf 2.'
            },
            {
                id: 'txt-lho-2',
                category: 'lho',
                categoryLabel: 'Teks LHO',
                title: 'Kelelawar Pemakan Buah (Codot) sebagai Penjaga Regenerasi Hutan',
                segments: [
                    {
                        tag: 'Pernyataan Umum / Klasifikasi',
                        tagColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-950 dark:text-emerald-300',
                        text: 'Kelelawar pemakan buah atau yang dikenal masyarakat dengan sebutan codot adalah satu-satunya mamalia yang memiliki kemampuan terbang sejati. Hewan ini tergolong ke dalam ordo Chiroptera dan subordo Megachiroptera yang aktif mencari makan pada malam hari (nokturnal).'
                    },
                    {
                        tag: 'Deskripsi Bagian',
                        tagColor: 'bg-blue-100 text-blue-800 dark:bg-blue-950 dark:text-blue-300',
                        text: 'Tubuh codot ditutupi oleh bulu halus berwarna cokelat kehitaman dengan rentang sayap yang dapat mencapai 40 hingga 70 sentimeter. Sayapnya tersusun dari selaput kulit tipis elastis yang membentang di antara jari-jari tungkai depan yang memanjang. Berbeda dengan kelelawar pemakan serangga yang mengandalkan ekolokasi, codot memiliki mata berukuran besar dengan penglihatan tajam serta indra penciuman yang sangat peka untuk mendeteksi buah matang.'
                    },
                    {
                        tag: 'Deskripsi Manfaat',
                        tagColor: 'bg-amber-100 text-amber-800 dark:bg-amber-950 dark:text-amber-300',
                        text: 'Dalam ekosistem hutan tropis, codot berperan vital sebagai agen penyerbuk bunga dan pemencar biji tumbuhan. Biji buah yang dimakan codot akan dikeluarkan kembali bersama kotorannya di lokasi yang jauh dari pohon induknya, sehingga membantu proses penghijauan alami hutan.'
                    }
                ],
                analysisNote: 'Kaidah Kebahasaan: Menggunakan kata nomina spesifik ("mamalia", "Chiroptera"), verba aktif ("terbang", "mencari", "membentang"), serta data ukuran objektif (40–70 cm).'
            },
            {
                id: 'txt-eks-1',
                category: 'eksposisi',
                categoryLabel: 'Teks Eksposisi',
                title: 'Urgensi Pengelolaan Sampah Plastik di Lingkungan Sekolah Menengah',
                segments: [
                    {
                        tag: 'Tesis (Pernyataan Pendapat)',
                        tagColor: 'bg-indigo-100 text-indigo-800 dark:bg-indigo-950 dark:text-indigo-300',
                        text: 'Pengurangan penggunaan plastik sekali pakai di lingkungan sekolah merupakan langkah mendesak yang harus segera diterapkan secara konsisten. Kebiasaan membawa botol minum (tumbler) dan wadah makan sendiri terbukti jauh lebih efektif menekan timbulan sampah dibandingkan sekadar menambah jumlah tempat sampah di sudut sekolah.'
                    },
                    {
                        tag: 'Argumentasi',
                        tagColor: 'bg-sky-100 text-sky-800 dark:bg-sky-950 dark:text-sky-300',
                        text: 'Berdasarkan data Kementerian Lingkungan Hidup dan Kehutanan (KLHK), sampah plastik menyumbang hampir 18% dari total timbulan sampah nasional, dan sebagian besar berasal dari kemasan makanan serta minuman instan. Di sekolah dengan populasi lebih dari seribu siswa, pembelian minuman kemasan gelas plastik setiap hari dapat menghasilkan ribuan limbah plastik dalam sepekan. Akibatnya, saluran drainase sekolah rawan tersumbat dan sampah plastik yang terurai menjadi mikroplastik berpotensi mencemari tanah serta air tanah di sekitar sekolah.'
                    },
                    {
                        tag: 'Penegasan Ulang',
                        tagColor: 'bg-teal-100 text-teal-800 dark:bg-teal-950 dark:text-teal-300',
                        text: 'Oleh karena itu, seluruh warga sekolah hendaknya membangun budaya minim sampah mulai dari hal sederhana. Kebijakan wajib membawa tumbler dan penerapan kantin bebas plastik sekali pakai tidak hanya menjaga kebersihan lingkungan sekolah, tetapi juga membentuk karakter pelajar yang peduli terhadap keberlanjutan bumi.'
                    }
                ],
                analysisNote: 'Identifikasi Struktur & Kaidah: Tesis memuat opini utama ("langkah mendesak..."). Argumentasi memuat kata perujukan ("Berdasarkan data KLHK"), angka statistik (18%), dan konjungsi kausalitas ("Akibatnya"). Penegasan ulang diawali "Oleh karena itu" dan kata persuasif ("hendaknya").'
            },
            {
                id: 'txt-eks-2',
                category: 'eksposisi',
                categoryLabel: 'Teks Eksposisi',
                title: 'Literasi Digital sebagai Benteng Pelajar Menghadapi Informasi Hoaks',
                segments: [
                    {
                        tag: 'Tesis (Pernyataan Pendapat)',
                        tagColor: 'bg-indigo-100 text-indigo-800 dark:bg-indigo-950 dark:text-indigo-300',
                        text: 'Penguatan literasi digital bagi pelajar SMA menjadi kebutuhan mutlak di tengah derasnya arus informasi media sosial. Kemampuan menyaring kebenaran berita jauh lebih krusial dibandingkan kecepatan membagikan informasi kepada orang lain.'
                    },
                    {
                        tag: 'Argumentasi',
                        tagColor: 'bg-sky-100 text-sky-800 dark:bg-sky-950 dark:text-sky-300',
                        text: 'Para pakar komunikasi menyimpulkan bahwa algoritma media sosial cenderung memprioritaskan konten yang memicu emosi kuat, seperti kemarahan atau ketakutan, sehingga berita bohong (hoaks) menyebar enam kali lebih cepat daripada fakta terverifikasi. Pelajar yang belum terbiasa melakukan verifikasi silang (cross-check) sangat rentan terpengaruh disinformasi kesehatan, penipuan daring, maupun ujaran kebencian yang memecah belah persatuan.'
                    },
                    {
                        tag: 'Penegasan Ulang',
                        tagColor: 'bg-teal-100 text-teal-800 dark:bg-teal-950 dark:text-teal-300',
                        text: 'Dengan demikian, sekolah dan keluarga perlu berkolaborasi melatih keterampilan berpikir kritis dalam bermedia digital. Membiasakan diri memeriksa kredibilitas sumber sebelum menekan tombol bagikan adalah wujud nyata tanggung jawab intelektual generasi muda.'
                    }
                ],
                analysisNote: 'Identifikasi Kaidah: Terdapat verba mental ("menyimpulkan", "terpengaruh"), istilah teknis ("algoritma", "disinformasi", "verifikasi"), dan konjungsi kausalitas ("sehingga").'
            },
            {
                id: 'txt-anek-1',
                category: 'anekdot',
                categoryLabel: 'Teks Anekdot',
                title: 'Kursi Empuk dan Janji Anti-Lupa',
                segments: [
                    {
                        tag: 'Abstraksi & Orientasi',
                        tagColor: 'bg-slate-200 text-slate-800 dark:bg-slate-800 dark:text-slate-200',
                        text: 'Pada suatu siang yang terik, dua orang sahabat lama, Budi dan Rian, sedang berbincang santai di warung kopi dekat alun-alun kota sambil membaca koran berita politik.'
                    },
                    {
                        tag: 'Krisis',
                        tagColor: 'bg-rose-100 text-rose-800 dark:bg-rose-950 dark:text-rose-300',
                        text: 'Budi mengerutkan kening lalu bertanya kepada Rian, "Yan, menurutmu kenapa ya banyak pejabat yang waktu kampanye ingatannya tajam sekali sampai hafal semua keluhan warga, tapi begitu duduk di kursi kantor langsung kena penyakit lupa ingatan?" Rian menyeruput kopinya lalu menjawab tenang, "Wah, kamu tidak tahu ya? Ternyata busa kursi empuk di gedung mewah itu mengandung medan magnet khusus yang bisa menyedot memori masa lalu!"'
                    },
                    {
                        tag: 'Reaksi & Koda',
                        tagColor: 'bg-amber-100 text-amber-800 dark:bg-amber-950 dark:text-amber-300',
                        text: 'Budi terbahak-bahak mendengar jawaban logis tapi nyeleneh itu, sementara bapak penjaga warung ikut tersenyum kecut sambil mengangguk-angguk setuju. Setelah itu, mereka pun melanjutkan obrolan sambil berharap kursi di kota mereka tidak mengandung magnet pelupa.'
                    }
                ],
                analysisNote: 'Analisis Anekdot: Kritik sosial ditujukan kepada pejabat yang melupakan janji kampanye setelah menjabat. Menggunakan kalimat retoris ("menurutmu kenapa ya..."), konjungsi waktu ("Setelah itu"), dan sindiran humoris tentang "busa kursi bermagnet".'
            },
            {
                id: 'txt-anek-2',
                category: 'anekdot',
                categoryLabel: 'Teks Anekdot',
                title: 'Lomba Kebersihan Tanpa Sampah',
                segments: [
                    {
                        tag: 'Orientasi',
                        tagColor: 'bg-slate-200 text-slate-800 dark:bg-slate-800 dark:text-slate-200',
                        text: 'Menjelang penilaian lomba kebersihan lingkungan antar-kelurahan, Pak RT mengumpulkan seluruh warga untuk kerja bakti massal sejak pukul enam pagi.'
                    },
                    {
                        tag: 'Krisis',
                        tagColor: 'bg-rose-100 text-rose-800 dark:bg-rose-950 dark:text-rose-300',
                        text: 'Selokan disikat bersih, jalanan disapu licin, dan tumpukan dedaunan serta plastik dikumpulkan dalam puluhan karung. Namun, karena truk pengangkut sampah belum datang, seorang warga bertanya, "Pak RT, karung-karung sampah ini mau ditaruh di mana? Tim juri sudah mau tiba!" Dengan penuh percaya diri Pak RT berseru, "Cepat pindahkan semua karung ini ke balik semak-semak perbatasan kelurahan sebelah, biar kelurahan kita terlihat paling bersih dan juara satu!"'
                    },
                    {
                        tag: 'Reaksi & Koda',
                        tagColor: 'bg-amber-100 text-amber-800 dark:bg-amber-950 dark:text-amber-300',
                        text: 'Para warga saling pandang dengan wajah melongo mendengar strategi "kebersihan" sang ketua RT. Akhirnya, bukannya mendapat piala, kelurahan mereka didiskualifikasi karena juri menemukan gunungan sampah bertuliskan nama RT mereka di balik semak perbatasan.'
                    }
                ],
                analysisNote: 'Analisis Anekdot: Menyindir budaya pencitraan (hanya ingin terlihat bersih di permukaan tetapi memindahkan masalah ke tempat lain). Terdapat kalimat seru/perintah ("Cepat pindahkan...!") dan kata kerja aksi ("disikat", "disapu", "pindahkan").'
            },
            {
                id: 'txt-hik-1',
                category: 'hikayat',
                categoryLabel: 'Teks Hikayat & STEM',
                title: 'Hikayat Nakhoda Muda & Misteri Kapal Tanpa Angin',
                segments: [
                    {
                        tag: 'Kutipan Hikayat (Bahasa Klasik)',
                        tagColor: 'bg-purple-100 text-purple-800 dark:bg-purple-950 dark:text-purple-300',
                        text: 'Hatta, maka berlayarlah Nakhoda Muda mengarungi samudra luas menuju negeri seberang membawa barang dagangan. Syahdan, di tengah lautan lepas, berhentilah angin bertiup selama tujuh hari tujuh malam sehingga kapal terkatung-katung tak bergerak. Segala awak kapal berputus asa, lalu berdoalah Nakhoda Muda memohon petunjuk kepada Tuhan Yang Maha Esa. Tak lama kemudian, Nakhoda Muda memerintahkan awak kapal membentangkan layar lebar dengan sudut serong serta memanfaatkan dayung panjang berporos kayu ulin secara berirama hingga kapal pun melaju perlahan menuju pulau terdekat.'
                    },
                    {
                        tag: 'Analisis Ciri & Nilai Hikayat',
                        tagColor: 'bg-indigo-100 text-indigo-800 dark:bg-indigo-950 dark:text-indigo-300',
                        text: '• Ciri Bahasa: Menggunakan kata arkais ("Hatta", "Syahdan", "mengarungi").\n• Nilai Religi: Tokoh tidak menyerah dan berdoa memohon pertolongan Tuhan.\n• Nilai Edukasi & Kepemimpinan: Nakhoda berpikir tenang dan kreatif memecahkan masalah saat krisis.'
                    },
                    {
                        tag: 'Penerapan dalam Pembelajaran STEM',
                        tagColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-950 dark:text-emerald-300',
                        text: '• Science (Fisika): Menganalisis gaya dorong (aksi-reaksi Hukum III Newton) saat dayung mendorong air ke belakang dan arah angin permukaan laut.\n• Engineering (Rekayasa): Desain tuas/pengungkit jenis pertama pada dayung berporos kayu ulin untuk memperbesar keuntungan mekanis.\n• Mathematics (Matematika): Menghitung rasio panjang lengan kuasa terhadap lengan beban dayung serta sudut kemiringan layar optimal.'
                    }
                ],
                analysisNote: 'Integrasi STEM membantu siswa memahami bahwa kecerdikan tokoh dalam hikayat klasik sesungguhnya menerapkan prinsip sains dan rekayasa terapan.'
            },
            {
                id: 'txt-hik-2',
                category: 'hikayat',
                categoryLabel: 'Teks Hikayat & STEM',
                title: 'Hikayat Putri Kemala & Ramuan Daun Dewa',
                segments: [
                    {
                        tag: 'Kutipan Hikayat (Bahasa Klasik)',
                        tagColor: 'bg-purple-100 text-purple-800 dark:bg-purple-950 dark:text-purple-300',
                        text: 'Alkisah, di sebuah kerajaan yang makmur, jatuh sakitlah Putri Kemala hingga tabib istana tiada sanggup mengobatinya. Maka bertitahlah Baginda Raja barang siapa dapat menyembuhkan sang putri akan diangkat menjadi menantu. Datanglah seorang pemuda desa yang arif membawa air rebusan daun sambiloto dan kunyit kuning yang telah disaring dengan kain sutra halus. Setelah diminumkan tiga kali sehari, atas izin Tuhan, pulihlah kesehatan Putri Kemala dengan seketika.'
                    },
                    {
                        tag: 'Analisis Ciri & Nilai Hikayat',
                        tagColor: 'bg-indigo-100 text-indigo-800 dark:bg-indigo-950 dark:text-indigo-300',
                        text: '• Ciri Hikayat: Istana sentris (raja, putri, tabib istana), kata arkais ("Alkisah", "bertitahlah", "tiada").\n• Nilai Sosial & Moral: Raja menepati janji tanpa memandang status sosial pemuda desa; pemuda desa tulus menolong sesama.'
                    },
                    {
                        tag: 'Penerapan dalam Pembelajaran STEM',
                        tagColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-950 dark:text-emerald-300',
                        text: '• Science (Biologi & Kimia): Mengidentifikasi senyawa aktif kurkumin pada kunyit dan andrografolid pada sambiloto sebagai antiinflamasi dan antibakteri alami.\n• Technology (Teknologi): Proses ekstraksi dan filtrasi (penyaringan dengan kain sutra) untuk memisahkan residu padat dari larutan zat aktif.\n• Mathematics: Menentukan dosis dan frekuensi pemberian obat (3 kali sehari) berdasarkan prinsip farmakokinetik sederhana.'
                    }
                ],
                analysisNote: 'Dari kisah ini siswa dapat menguji hipotesis ilmiah kandungan tanaman herbal Nusantara yang diwariskan dalam karya sastra klasik.'
            }
        ];

        // ==========================================
        // 3. BANK SOAL LATIHAN KUSTOM (24 SOAL)
        // ==========================================
        const QUIZ_BANK = [
            // --- LHO (6 Soal) ---
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                passage: 'Hutan mangrove adalah tipe hutan yang tumbuh di daerah pasang surut pantai yang berlumpur. Ekosistem ini memiliki kemampuan adaptasi tinggi terhadap kadar garam (salinitas) air laut.',
                question: 'Berdasarkan struktur Teks Laporan Hasil Observasi (LHO), kutipan paragraf di atas termasuk ke dalam bagian...',
                options: ['Deskripsi bagian', 'Pernyataan umum / klasifikasi', 'Deskripsi manfaat', 'Argumentasi ilmiah', 'Penegasan ulang'],
                answer: 1,
                explanation: 'Paragraf tersebut berisi definisi umum ("Hutan mangrove adalah...") dan klasifikasi habitatnya secara garis besar, sehingga merupakan bagian Pernyataan Umum / Klasifikasi.'
            },
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                passage: 'Data Pengamatan Pohon Sagu:\n- Tinggi batang: 10–15 meter\n- Diameter batang: 35–50 cm\n- Warna kulit batang: cokelat keabu-abuan dan keras\n- Bagian dalam batang: berisi empulur putih kaya pati',
                question: 'Manakah kalimat deskripsi bagian yang paling tepat dan objektif berdasarkan data observasi di atas?',
                options: [
                    'Pohon sagu sangat bermanfaat bagi masyarakat Sulawesi Tenggara sebagai makanan pokok pengganti nasi.',
                    'Pohon sagu merupakan tumbuhan palma penghasil karbohidrat yang tumbuh subur di daerah rawa air tawar.',
                    'Batang pohon sagu memiliki tinggi 10 hingga 15 meter dengan diameter 35–50 cm, berkulit cokelat keabu-abuan yang keras, serta menyimpan empulur putih kaya pati di bagian dalamnya.',
                    'Sebaiknya pemerintah melestarikan pohon sagu karena pohon ini terlihat sangat kokoh dan indah dipandang.',
                    'Menurut warga lokal, pohon sagu yang tinggi batangnya 15 meter pasti memiliki rasa pati yang lebih manis.'
                ],
                answer: 2,
                explanation: 'Pilihan C merangkum seluruh data faktual (tinggi, diameter, warna kulit, isi empulur) secara objektif tanpa opini subjektif, sesuai kaidah Deskripsi Bagian LHO.'
            },
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                question: 'Perhatikan kalimat berikut: "Terumbu karang berfungsi sebagai pemecah gelombang alami yang mencegah abrasi pantai." Dalam struktur teks LHO, kalimat tersebut tepat diletakkan pada bagian...',
                options: ['Pernyataan umum', 'Deskripsi bagian', 'Deskripsi manfaat', 'Orientasi', 'Tesis'],
                answer: 2,
                explanation: 'Kata kunci "berfungsi sebagai..." menunjukkan kegunaan atau dampak positif objek bagi lingkungan, yang merupakan inti dari Deskripsi Manfaat.'
            },
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                question: 'Manakah di bawah ini yang merupakan contoh kalimat definisi yang lazim ditemukan pada teks LHO?',
                options: [
                    'Daun sirih berbentuk menyerupai jantung dengan ujung meruncing.',
                    'Komodo memiliki panjang tubuh yang dapat mencapai tiga meter.',
                    'Wayang adalah seni pertunjukan tradisional asli Indonesia yang telah ditetapkan UNESCO sebagai warisan budaya.',
                    'Pada malam hari, burung hantu berburu mangsa di antara pepohonan.',
                    'Akar bakau menjulang tinggi untuk menopang batang dari terjangan ombak.'
                ],
                answer: 2,
                explanation: 'Kalimat definisi ditandai dengan penggunaan verba relasional penghubung seperti "adalah", "merupakan", "ialah", atau "yakni".'
            },
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                question: 'Sifat utama informasi yang disajikan dalam Teks Laporan Hasil Observasi (LHO) haruslah...',
                options: ['Imajinatif dan menghibur', 'Subjektif sesuai perasaan penulis', 'Objektif, faktual, dan sistematis', 'Persuasif memengaruhi pembaca', 'Kontroversial dan penuh sindiran'],
                answer: 2,
                explanation: 'Teks LHO disusun berdasarkan pengamatan langsung sehingga harus objektif (sesuai kenyataan), faktual (berdasarkan fakta), dan sistematis.'
            },
            {
                topic: 'lho',
                topicLabel: 'Teks LHO',
                question: 'Kata kerja yang digunakan untuk menjelaskan klasifikasi atau definisi dalam teks LHO (seperti: merupakan, digolongkan, termasuk) disebut...',
                options: ['Verba mental', 'Verba relasional', 'Verba tingkah laku', 'Konjungsi kausalitas', 'Kata arkais'],
                answer: 1,
                explanation: 'Verba relasional adalah kata kerja yang berfungsi sebagai penghubung antara subjek dan pelengkap untuk menyatakan definisi atau klasifikasi.'
            },

            // --- EKSPOSISI (6 Soal) ---
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                passage: 'Penerapan transportasi umum berbasis listrik di kota-kota besar merupakan solusi strategis untuk menekan polusi udara. Menurut data dinas lingkungan hidup, sektor transportasi menyumbang lebih dari 60% emisi karbon perkotaan. Dengan beralih ke bus listrik, emisi gas buang dapat dipangkas secara signifikan.',
                question: 'Kalimat pertama pada kutipan teks eksposisi di atas merupakan bagian...',
                options: ['Argumentasi', 'Tesis (pernyataan pendapat)', 'Penegasan ulang', 'Deskripsi bagian', 'Abstraksi'],
                answer: 1,
                explanation: 'Kalimat pertama menyatakan sikap/pendapat utama penulis ("merupakan solusi strategis untuk menekan polusi udara"), yang menjadi Tesis.'
            },
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                question: 'Urutan struktur Teks Eksposisi yang tepat adalah...',
                options: [
                    'Pernyataan umum – Deskripsi bagian – Deskripsi manfaat',
                    'Abstraksi – Orientasi – Krisis – Reaksi – Koda',
                    'Tesis – Argumentasi – Penegasan ulang',
                    'Orientasi – Komplikasi – Resolusi – Koda',
                    'Tujuan – Langkah-langkah – Penegasan ulang'
                ],
                answer: 2,
                explanation: 'Teks Eksposisi memiliki tiga struktur inti: Tesis (pendapat awal), Argumentasi (bukti/alasan), dan Penegasan Ulang (simpulan/rekomendasi).'
            },
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                passage: 'Penggunaan gawai secara berlebihan sebelum tidur mengganggu produksi hormon melatonin. Akibatnya, kualitas tidur remaja menurun dan konsentrasi belajar di sekolah ikut terganggu.',
                question: 'Kata "Akibatnya" dalam kutipan teks eksposisi tersebut termasuk kaidah kebahasaan berupa...',
                options: ['Konjungsi temporal', 'Konjungsi kausalitas', 'Kata kerja mental', 'Kata perujukan', 'Kalimat retoris'],
                answer: 1,
                explanation: 'Konjungsi kausalitas (sebab, karena, sehingga, akibatnya, oleh karena itu) digunakan untuk menunjukkan hubungan sebab-akibat dalam argumen eksposisi.'
            },
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                question: 'Fungsi utama bagian Argumentasi dalam Teks Eksposisi adalah...',
                options: [
                    'Menyampaikan kelucuan untuk menyindir pihak tertentu',
                    'Memperkuat dan membuktikan kebenaran tesis dengan fakta, data, dan alasan logis',
                    'Menggambarkan ciri fisik suatu benda secara terperinci',
                    'Menceritakan asal-usul suatu kerajaan pada masa lampau',
                    'Menutup tulisan dengan ucapan terima kasih kepada pembaca'
                ],
                answer: 1,
                explanation: 'Argumentasi berisi bukti empiris, data statistik, pendapat ahli, dan penalaran logis untuk mendukung tesis yang diajukan penulis.'
            },
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                question: 'Manakah kalimat yang mengandung kata kerja mental (verba mental) dalam teks eksposisi?',
                options: [
                    'Petani memanen padi di sawah pada pagi hari.',
                    'Para peneliti menyimpulkan bahwa kebiasaan membaca meningkatkan daya analisis siswa.',
                    'Air sungai meluap setelah hujan deras mengguyur kota.',
                    'Siswa SMAN 4 Kendari berbaris rapi di lapangan upacara.',
                    'Kendaraan bermotor melintas di jembatan Teluk Kendari.'
                ],
                answer: 1,
                explanation: 'Kata "menyimpulkan" menggambarkan aktivitas berpikir/kognitif (verba mental), bukan tindakan fisik.'
            },
            {
                topic: 'eksposisi',
                topicLabel: 'Teks Eksposisi',
                question: 'Bagian akhir teks eksposisi yang merangkum kembali tesis dengan kalimat berbeda serta memuat saran atau ajakan disebut...',
                options: ['Penegasan ulang (reiterasi)', 'Krisis', 'Koda', 'Klasifikasi umum', 'Orientasi'],
                answer: 0,
                explanation: 'Penegasan ulang (reiterasi) berfungsi menegaskan kembali pendapat penulis di awal berdasarkan argumen yang telah dipaparkan.'
            },

            // --- ANEKDOT (6 Soal) ---
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                question: 'Perbedaan mendasar antara Teks Anekdot dengan teks humor biasa terletak pada...',
                options: [
                    'Teks anekdot selalu berbentuk puisi lama',
                    'Teks anekdot mengandung kritik sosial atau sindiran terhadap fenomena publik/layanan masyarakat',
                    'Teks anekdot tidak memiliki tokoh dan alur cerita',
                    'Teks anekdot hanya menceritakan hewan yang bisa berbicara',
                    'Teks anekdot wajib menggunakan bahasa Melayu klasik'
                ],
                answer: 1,
                explanation: 'Teks anekdot tidak sekadar memancing tawa, melainkan menyisipkan kritik sosial atau sindiran halus mengenai kebijakan, layanan publik, atau perilaku sosial.'
            },
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                question: 'Bagian dalam struktur teks anekdot yang menjadi puncak munculnya kekonyolan sekaligus inti sindiran disebut...',
                options: ['Abstraksi', 'Orientasi', 'Krisis', 'Reaksi', 'Koda'],
                answer: 2,
                explanation: 'Krisis adalah bagian paling krusial dalam anekdot karena di sinilah muncul hal unik, konyol, atau sindiran tajam.'
            },
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                passage: '"Sudah tahu jalanan ini berlubang seperti kolam lele, masih saja anggaran perbaikannya hilang entah ke mana?" tanya seorang warga sambil geleng-geleng kepala.',
                question: 'Kalimat yang diucapkan warga pada kutipan anekdot tersebut menggunakan kaidah kebahasaan berupa...',
                options: ['Kalimat definisi', 'Kalimat retoris', 'Verba relasional', 'Konjungsi kausalitas', 'Istilah biologi'],
                answer: 1,
                explanation: 'Kalimat retoris adalah pertanyaan yang tidak membutuhkan jawaban nyata, melainkan bertujuan menyindir atau menegaskan suatu keadaan.'
            },
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                question: 'Tanggapan tokoh lain terhadap kekonyolan atau sindiran yang muncul pada bagian krisis dalam teks anekdot disebut...',
                options: ['Abstraksi', 'Orientasi', 'Komplikasi', 'Reaksi', 'Tesis'],
                answer: 3,
                explanation: 'Reaksi adalah respons (tertawa, terkejut, heran, atau tersipu) yang muncul tepat setelah peristiwa krisis.'
            },
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                question: 'Urutan struktur Teks Anekdot yang lengkap dan sistematis adalah...',
                options: [
                    'Orientasi – Krisis – Reaksi – Abstraksi – Koda',
                    'Abstraksi – Orientasi – Krisis – Reaksi – Koda',
                    'Tesis – Krisis – Reaksi – Penegasan ulang',
                    'Abstraksi – Tesis – Argumentasi – Koda',
                    'Pernyataan umum – Krisis – Reaksi – Simpulan'
                ],
                answer: 1,
                explanation: 'Struktur lengkap teks anekdot berurutan dari Abstraksi -> Orientasi -> Krisis -> Reaksi -> Koda.'
            },
            {
                topic: 'anekdot',
                topicLabel: 'Teks Anekdot',
                question: 'Kata-kata seperti "pada suatu hari", "kemudian", "setelah itu", dan "akhirnya" dalam teks anekdot berfungsi sebagai...',
                options: ['Konjungsi waktu (temporal)', 'Verba mental', 'Kata perujukan', 'Kata arkais', 'Verba relasional'],
                answer: 0,
                explanation: 'Teks anekdot berbentuk narasi/cerita sehingga menggunakan konjungsi temporal untuk mengurutkan kronologi peristiwa.'
            },

            // --- HIKAYAT & STEM (6 Soal) ---
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                passage: 'Syahdan, lahirlah seorang putra raja yang keluar dari dalam buluh betung serta langsung pandai berbicara dan memanah dengan tepat.',
                question: 'Ciri khas teks hikayat yang paling menonjol pada kutipan di atas adalah...',
                options: ['Realistis dan ilmiah', 'Kemustahilan dan kesaktian tokoh', 'Berlatar kehidupan modern', 'Menggunakan bahasa gaul', 'Nama pengarang dicantumkan jelas'],
                answer: 1,
                explanation: 'Bayi lahir dari bambu dan langsung bisa memanah merupakan ciri kemustahilan (tidak masuk akal) sekaligus kesaktian tokoh dalam hikayat.'
            },
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                question: 'Istilah "Anonim" sebagai salah satu ciri teks hikayat bermakna...',
                options: [
                    'Cerita berpusat pada kehidupan di dalam istana',
                    'Terdapat cerita lain di dalam cerita utama',
                    'Nama pengarangnya tidak diketahui karena disebarkan secara lisan turun-temurun',
                    'Menggunakan kosakata bahasa asing modern',
                    'Memiliki akhir cerita yang selalu menyedihkan'
                ],
                answer: 2,
                explanation: 'Anonim berarti tidak diketahui identitas penulisnya karena sastra Melayu klasik awalnya merupakan tradisi lisan milik bersama.'
            },
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                passage: 'Dalam sebuah hikayat, seorang tabib istana meramu ekstrak kulit kayu manis dan jahe merah untuk mengobati demam prajurit kerajaan melalui proses perebusan dan penyaringan.',
                question: 'Jika dikaitkan dengan pembelajaran STEM (Science, Technology, Engineering, Mathematics), aktivitas tabib tersebut dapat dikaji dalam bidang...',
                options: [
                    'Astronomi dan tata surya',
                    'Sains (fitokimia senyawa aktif tanaman) dan Teknologi (teknik ekstraksi/filtrasi)',
                    'Geometri ruang tiga dimensi',
                    'Pemrograman jaringan komputer',
                    'Mekanika kuantum partikel'
                ],
                answer: 1,
                explanation: 'Kandungan senyawa obat dalam rempah dikaji dalam Sains (Biologi/Kimia), sedangkan proses perebusan dan penyaringan merupakan penerapan Teknologi proses sederhana.'
            },
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                passage: 'Meskipun telah menjadi raja yang berkuasa, Baginda tetap berlaku adil kepada rakyat jelata, suka bermusyawarah dengan para menteri, serta rajin beribadah.',
                question: 'Nilai-nilai yang terkandung dalam kutipan hikayat tersebut adalah...',
                options: [
                    'Nilai estetika dan nilai ekonomi',
                    'Nilai sosial, nilai budaya (musyawarah), dan nilai religi',
                    'Nilai individualisme dan materialisme',
                    'Nilai olahraga dan kesehatan',
                    'Nilai teknologi informasi'
                ],
                answer: 1,
                explanation: 'Berlaku adil kepada rakyat mencerminkan nilai sosial, musyawarah mencerminkan nilai budaya, dan rajin beribadah mencerminkan nilai religi.'
            },
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                question: 'Kata-kata seperti "hatta", "syahdan", "alkisah", "titah", dan "mahligai" dalam teks hikayat termasuk kosakata...',
                options: ['Serapan bahasa Inggris', 'Istilah teknis kedokteran', 'Kata arkais (bahasa Melayu klasik)', 'Bahasa jurnalistik modern', 'Singkatan baku'],
                answer: 2,
                explanation: 'Kata arkais adalah kosakata kuno dari bahasa Melayu klasik yang menjadi penanda khas teks hikayat.'
            },
            {
                topic: 'hikayat',
                topicLabel: 'Teks Hikayat & STEM',
                passage: 'Dalam kisah Hikayat Abu Nawas, tokoh cerdik tersebut diminta memindahkan istana raja. Ia pun mengajak warga menghitung jumlah batu bata istana dan merancang sistem katrol kayu untuk menguji gaya angkat beban.',
                question: 'Penerapan aspek Engineering (Rekayasa) dan Mathematics dalam pembelajaran STEM dari kisah tersebut adalah...',
                options: [
                    'Menghafal seluruh nama raja di dunia',
                    'Merancang sistem mekanik katrol untuk memperkecil gaya angkat serta menghitung estimasi volume/jumlah material',
                    'Menulis ulang hikayat menggunakan tinta emas',
                    'Mewarnai gambar istana dengan cat air',
                    'Membaca puisi di depan kelas'
                ],
                answer: 1,
                explanation: 'Perancangan sistem katrol merupakan bagian dari Engineering (Rekayasa), sedangkan perhitungan estimasi jumlah material merupakan penerapan Mathematics.'
            }
        ];

        // ==========================================
        // 4. FLASHCARDS & ACTIVE RECALL DATA
        // ==========================================
        const FLASHCARDS_DATA = [
            { id: 'fc-1', topic: 'lho', tag: 'TEKS LHO', front: 'Apa 3 struktur utama Teks Laporan Hasil Observasi (LHO)?', back: '1. Pernyataan Umum / Klasifikasi (definisi & info umum)\n2. Deskripsi Bagian (perincian fisik/bagian objek)\n3. Deskripsi Manfaat (fungsi/kegunaan objek).' },
            { id: 'fc-2', topic: 'lho', tag: 'TEKS LHO', front: 'Apa perbedaan Kalimat Definisi dan Kalimat Deskripsi?', back: 'Kalimat Definisi menjelaskan pengertian umum objek (memakai kata: adalah, merupakan, yaitu). Kalimat Deskripsi menggambarkan ciri fisik/sifat objek secara rinci (warna, ukuran, bentuk).' },
            { id: 'fc-3', topic: 'lho', tag: 'TEKS LHO', front: 'Sebutkan 4 kaidah kebahasaan utama Teks LHO!', back: '1. Kata/frasa nomina (kata benda)\n2. Verba relasional (adalah, merupakan, tergolong)\n3. Verba aktif (tumbuh, hidup, menyerap)\n4. Istilah keilmuan/teknis.' },
            { id: 'fc-4', topic: 'lho', tag: 'TEKS LHO', front: 'Bagaimana aturan mengubah tabel data menjadi paragraf deskripsi LHO?', back: 'Ubah seluruh poin data angka dan fakta menjadi kalimat efektif yang padu, objektif, tidak memasukkan opini pribadi, serta menggunakan istilah teknis yang tepat.' },
            
            { id: 'fc-5', topic: 'eksposisi', tag: 'TEKS EKSPOSISI', front: 'Sebutkan struktur Teks Eksposisi secara berurutan!', back: '1. Tesis (Pernyataan Pendapat)\n2. Argumentasi (Fakta, data, alasan logis)\n3. Penegasan Ulang / Reiterasi (Simpulan & saran).' },
            { id: 'fc-6', topic: 'eksposisi', tag: 'TEKS EKSPOSISI', front: 'Bagaimana cara cepat mengidentifikasi bagian Tesis dalam Teks Eksposisi?', back: 'Periksa paragraf pertama dan temukan kalimat opini utama atau sudut pandang penulis terhadap isu yang dibahas.' },
            { id: 'fc-7', topic: 'eksposisi', tag: 'TEKS EKSPOSISI', front: 'Apa itu Verba Mental dan contohnya dalam Teks Eksposisi?', back: 'Verba mental adalah kata kerja yang menggambarkan respons pemikiran/batin. Contoh: berpendapat, menyimpulkan, meyakini, memperkirakan, mengkritisi.' },
            { id: 'fc-8', topic: 'eksposisi', tag: 'TEKS EKSPOSISI', front: 'Sebutkan contoh Konjungsi Kausalitas dan Kata Perujukan!', back: 'Konjungsi kausalitas: sebab, karena, sehingga, akibatnya, oleh karena itu.\nKata perujukan: berdasarkan data..., menurut penelitian..., merujuk pada...' },

            { id: 'fc-9', topic: 'anekdot', tag: 'TEKS ANEKDOT', front: 'Sebutkan 5 struktur lengkap Teks Anekdot!', back: '1. Abstraksi (gambaran awal)\n2. Orientasi (pengenalan tokoh/latar)\n3. Krisis (puncak kelucuan/sindiran)\n4. Reaksi (tanggapan tokoh)\n5. Koda (penutup cerita).' },
            { id: 'fc-10', topic: 'anekdot', tag: 'TEKS ANEKDOT', front: 'Apa tujuan utama penulisan Teks Anekdot?', back: 'Menyampaikan kritik sosial atau sindiran halus terhadap fenomena masyarakat/layanan publik yang dikemas melalui cerita singkat yang lucu.' },
            { id: 'fc-11', topic: 'anekdot', tag: 'TEKS ANEKDOT', front: 'Apa yang dimaksud dengan Kalimat Retoris dalam Teks Anekdot?', back: 'Kalimat tanya yang tidak memerlukan jawaban karena jawabannya sudah diketahui bersama atau digunakan untuk menyindir.' },
            { id: 'fc-12', topic: 'anekdot', tag: 'TEKS ANEKDOT', front: 'Apa perbedaan bagian Krisis dan Reaksi pada Anekdot?', back: 'Krisis adalah bagian munculnya masalah unik/kekonyolan/sindiran, sedangkan Reaksi adalah tanggapan atau respons tokoh lain terhadap krisis tersebut.' },

            { id: 'fc-13', topic: 'hikayat', tag: 'TEKS HIKAYAT', front: 'Sebutkan 6 ciri khas Teks Hikayat!', back: '1. Kemustahilan\n2. Kesaktian tokoh\n3. Anonim (tanpa nama pengarang)\n4. Istana sentris\n5. Alur berbingkai\n6. Bahasa Melayu klasik (kata arkais).' },
            { id: 'fc-14', topic: 'hikayat', tag: 'TEKS HIKAYAT', front: 'Apa arti kata arkais: Hatta, Syahdan, Titah, dan Mahligai?', back: '• Hatta = lalu / maka\n• Syahdan = selanjutnya / kemudian\n• Titah = perintah raja\n• Mahligai = tempat kediaman raja/putri (istana).' },
            { id: 'fc-15', topic: 'hikayat', tag: 'TEKS HIKAYAT', front: 'Sebutkan 5 nilai kehidupan yang terkandung dalam Teks Hikayat!', back: '1. Nilai Religi (keagamaan)\n2. Nilai Moral (budi pekerti)\n3. Nilai Sosial (kepedulian sesama)\n4. Nilai Budaya (adat istiadat)\n5. Nilai Edukasi (pendidikan/kecerdikan).' },
            { id: 'fc-16', topic: 'hikayat', tag: 'HIKAYAT & STEM', front: 'Bagaimana penerapan Teks Hikayat dalam pembelajaran STEM?', back: 'Mengkaji fenomena dalam cerita secara ilmiah: Sains (khasiat herbal/hukum fisika), Teknologi (proses filtrasi/media digital), Rekayasa (desain alat/katrol), dan Matematika (logika hitung & rasio).' }
        ];

        const ACTIVE_RECALL_PROMPTS = [
            { tag: 'TEKS LHO', prompt: 'Tuliskan 3 struktur Teks LHO beserta fungsi singkat masing-masing bagian!', answer: '1. Pernyataan Umum/Klasifikasi: berisi definisi dan pengelompokan umum objek.\n2. Deskripsi Bagian: merinci bagian fisik, ukuran, warna, atau ciri khusus objek secara objektif.\n3. Deskripsi Manfaat: menjelaskan kegunaan atau fungsi objek bagi manusia/alam.' },
            { tag: 'TEKS EKSPOSISI', prompt: 'Bagaimana cara membedakan bagian Tesis, Argumentasi, dan Penegasan Ulang saat membaca soal Teks Eksposisi?', answer: '• Tesis berada di awal paragraf berupa opini utama penulis terhadap suatu isu.\n• Argumentasi berada di tengah berisi bukti, fakta lapangan, angka statistik, atau kutipan ahli.\n• Penegasan Ulang berada di akhir berisi rangkuman tesis dengan kalimat baru serta saran/rekomendasi (sering memakai "oleh karena itu").' },
            { tag: 'TEKS ANEKDOT', prompt: 'Jelaskan struktur Teks Anekdot (Abstraksi, Orientasi, Krisis, Reaksi, Koda) dan tunjukkan bagian mana yang memuat kritik sosial!', answer: 'Abstraksi (pembuka singkat), Orientasi (pengenalan tokoh/latar), Krisis (munculnya kelucuan/masalah—di sinilah inti kritik sosial/sindiran berada), Reaksi (respons tokoh atas krisis), dan Koda (penutup).'},
            { tag: 'TEKS HIKAYAT', prompt: 'Sebutkan minimal 5 ciri Teks Hikayat dan jelaskan maksud dari "Istana Sentris" dan "Alur Berbingkai"!', answer: 'Ciri: kemustahilan, kesaktian, anonim, istana sentris, alur berbingkai, bahasa Melayu klasik.\n• Istana sentris: latar tempat dan tokoh berpusat di lingkungan kerajaan.\n• Alur berbingkai: di dalam sebuah cerita utama terdapat tokoh yang bercerita lagi (cerita di dalam cerita).' },
            { tag: 'HIKAYAT & STEM', prompt: 'Berikan contoh konkret bagaimana unsur atau peristiwa dalam Teks Hikayat dapat diterapkan dalam pembelajaran STEM (Sains, Teknologi, Rekayasa, Matematika)!', answer: 'Contoh: Pada kisah tabib meramu obat herbal atau nakhoda menggerakkan kapal:\n• Sains: Menganalisis senyawa bioaktif tanaman obat atau gaya dorong hukum Newton.\n• Teknologi: Proses ekstraksi/penyaringan larutan atau membuat simulasi animasi cerita.\n• Rekayasa (Engineering): Merancang mekanisme tuas/katrol sederhana.\n• Matematika: Menghitung takaran dosis, rasio keuntungan mekanis, atau teka-teki logika pembagian.' }
        ];

        // ==========================================
        // 5. STATE MANAGEMENT & LOCAL STORAGE
        // ==========================================
        let appState = {
            completedTopics: JSON.parse(localStorage.getItem('sman4_completed_topics') || '[]'),
            masteredFlashcards: JSON.parse(localStorage.getItem('sman4_mastered_fc') || '[]'),
            bestQuizScore: localStorage.getItem('sman4_best_quiz') || null,
            currentTopic: 'lho',
            currentTextFilter: 'all',
            // Flashcard & Recall states
            filteredFC: [...FLASHCARDS_DATA],
            currentFCIndex: 0,
            isFCFlipped: false,
            currentARIndex: 0,
            // Quiz states
            quizQuestions: [],
            quizAnswers: {},
            quizCurrentIdx: 0,
            quizTimerInterval: null,
            quizSecondsLeft: 0
        };

        function saveState() {
            localStorage.setItem('sman4_completed_topics', JSON.stringify(appState.completedTopics));
            localStorage.setItem('sman4_mastered_fc', JSON.stringify(appState.masteredFlashcards));
            if (appState.bestQuizScore !== null) {
                localStorage.setItem('sman4_best_quiz', appState.bestQuizScore);
            }
            updateProgressUI();
        }

        function resetAllProgress() {
            appState.completedTopics = [];
            appState.masteredFlashcards = [];
            appState.bestQuizScore = null;
            localStorage.removeItem('sman4_completed_topics');
            localStorage.removeItem('sman4_mastered_fc');
            localStorage.removeItem('sman4_best_quiz');
            updateProgressUI();
            renderTopicDetail(appState.currentTopic);
            renderFlashcard();
            showToast('Progres belajar berhasil direset.', 'info');
        }

        function updateProgressUI() {
            const topicCount = appState.completedTopics.length;
            const fcCount = appState.masteredFlashcards.length;
            const totalFC = FLASHCARDS_DATA.length;
            const quizText = appState.bestQuizScore !== null ? `${appState.bestQuizScore}` : '-';

            document.getElementById('stat-materi-top').textContent = `${topicCount}/4`;
            document.getElementById('stat-fc-top').textContent = `${fcCount}`;
            document.getElementById('stat-quiz-top').textContent = quizText;

            document.getElementById('hero-stat-materi').textContent = `${topicCount} / 4`;
            document.getElementById('hero-stat-fc').textContent = `${fcCount} / ${totalFC}`;
            document.getElementById('hero-stat-quiz').textContent = quizText;

            // Calculate overall percentage (40% topics, 40% flashcards, 20% quiz)
            const topicPct = (topicCount / 4) * 40;
            const fcPct = (fcCount / totalFC) * 40;
            const quizPct = appState.bestQuizScore !== null ? (Number(appState.bestQuizScore) / 100) * 20 : 0;
            const totalPct = Math.min(100, Math.round(topicPct + fcPct + quizPct));

            document.getElementById('overall-progress-bar').style.width = `${Math.max(5, totalPct)}%`;
            document.getElementById('overall-progress-text').textContent = `${totalPct}% Siap Ujian`;
        }

        // ==========================================
        // 6. UI NAVIGATION & THEME HANDLING
        // ==========================================
        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            const bgColors = {
                success: 'bg-emerald-600 text-white',
                info: 'bg-sman4-800 text-white',
                warning: 'bg-amber-500 text-slate-950'
            };
            toast.className = `${bgColors[type] || bgColors.info} px-4 py-3 rounded-xl shadow-lg text-sm font-semibold flex items-center gap-2 fade-in pointer-events-auto`;
            toast.innerHTML = `<i data-lucide="info" class="w-4 h-4 shrink-0"></i><span>${message}</span>`;
            container.appendChild(toast);
            lucide.createIcons();
            setTimeout(() => {
                toast.style.opacity = '0';
                toast.style.transition = 'opacity 0.3s';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // Tab Navigation
        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const targetTab = btn.getAttribute('data-tab');
                switchTab(targetTab);
                // Close mobile sidebar if open
                closeMobileSidebar();
            });
        });

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById(`tab-${tabId}`).classList.remove('hidden');

            document.querySelectorAll('.nav-btn').forEach(btn => {
                if (btn.getAttribute('data-tab') === tabId) {
                    btn.className = 'nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold transition-all bg-sman4-800 text-white shadow-md shadow-sman4-800/20';
                } else {
                    btn.className = 'nav-btn w-full flex items-center gap-3 px-3.5 py-3 rounded-xl text-sm font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all';
                }
            });
            lucide.createIcons();
        }

        // Mobile Sidebar Controls
        const sidebar = document.getElementById('sidebar');
        const backdrop = document.getElementById('sidebar-backdrop');
        document.getElementById('mobile-menu-btn').addEventListener('click', () => {
            sidebar.classList.remove('-translate-x-full');
            backdrop.classList.remove('hidden');
        });
        function closeMobileSidebar() {
            sidebar.classList.add('-translate-x-full');
            backdrop.classList.add('hidden');
        }
        document.getElementById('close-sidebar-btn').addEventListener('click', closeMobileSidebar);
        backdrop.addEventListener('click', closeMobileSidebar);

        // Dark Mode Toggle
        document.getElementById('theme-toggle').addEventListener('click', () => {
            document.documentElement.classList.toggle('dark');
            const isDark = document.documentElement.classList.contains('dark');
            localStorage.setItem('sman4_theme', isDark ? 'dark' : 'light');
        });
        if (localStorage.getItem('sman4_theme') === 'dark') {
            document.documentElement.classList.add('dark');
        }

        // ==========================================
        // 7. TAB 1: RENDER STUDY HUB (MATERI)
        // ==========================================
        function selectTopic(topicId) {
            appState.currentTopic = topicId;
            document.querySelectorAll('.topic-pill').forEach(btn => {
                btn.className = 'topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 flex items-center justify-center gap-2';
            });
            const activeBtn = document.getElementById(`topic-btn-${topicId}`);
            activeBtn.className = 'topic-pill flex-1 min-w-[140px] py-2.5 px-4 rounded-xl text-sm font-bold transition-all bg-sman4-800 text-white shadow-xs flex items-center justify-center gap-2';
            renderTopicDetail(topicId);
        }

        function toggleTopicComplete(topicId) {
            const idx = appState.completedTopics.indexOf(topicId);
            if (idx === -1) {
                appState.completedTopics.push(topicId);
                showToast('Materi ditandai sudah dikuasai!', 'success');
            } else {
                appState.completedTopics.splice(idx, 1);
                showToast('Tanda selesai dibatalkan.', 'info');
            }
            saveState();
            renderTopicDetail(topicId);
        }

        function renderTopicDetail(topicId) {
            const data = CURRICULUM_DATA[topicId];
            const isCompleted = appState.completedTopics.includes(topicId);
            const container = document.getElementById('topic-detail-container');

            let structuresHTML = data.structures.map(st => `
                <div class="p-4 sm:p-5 rounded-xl bg-slate-50 dark:bg-slate-800/70 border border-slate-200/80 dark:border-slate-700/80 space-y-2">
                    <h4 class="font-display font-bold text-base text-sman4-800 dark:text-emas-400">${st.name}</h4>
                    <p class="text-sm text-slate-700 dark:text-slate-300 leading-relaxed whitespace-pre-line">${st.desc}</p>
                    ${st.clue ? `<div class="inline-block mt-1 px-3 py-1 rounded-lg bg-amber-100/80 dark:bg-amber-950/60 text-amber-900 dark:text-amber-300 text-xs font-semibold">${st.clue}</div>` : ''}
                </div>
            `).join('');

            let kaidahHTML = data.kaidah.map(kd => `
                <div class="flex items-start gap-3 p-3.5 rounded-xl border border-slate-200/70 dark:border-slate-800 bg-white dark:bg-slate-900/50">
                    <div class="w-6 h-6 rounded-full bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-indigo-300 flex items-center justify-center shrink-0 mt-0.5">
                        <i data-lucide="check" class="w-3.5 h-3.5"></i>
                    </div>
                    <div>
                        <h5 class="font-bold text-sm text-slate-900 dark:text-white">${kd.title}</h5>
                        <p class="text-xs sm:text-sm text-slate-600 dark:text-slate-400 mt-0.5 leading-relaxed">${kd.detail}</p>
                    </div>
                </div>
            `).join('');

            // Special LHO Data-to-Paragraph Workshop
            let workshopHTML = '';
            if (data.dataWorkshop) {
                const ws = data.dataWorkshop;
                const rows = ws.tableRows.map(r => `
                    <tr class="border-b border-slate-200 dark:border-slate-700">
                        <td class="py-2.5 px-4 font-semibold text-slate-800 dark:text-slate-200 bg-slate-50/70 dark:bg-slate-800/40 w-1/3">${r[0]}</td>
                        <td class="py-2.5 px-4 text-slate-600 dark:text-slate-300">${r[1]}</td>
                    </tr>
                `).join('');

                workshopHTML = `
                <div class="bg-gradient-to-br from-emerald-50 to-teal-50/60 dark:from-emerald-950/30 dark:to-slate-900 p-6 rounded-2xl border border-emerald-200 dark:border-emerald-800/50 space-y-4">
                    <div class="flex items-center gap-2 text-emerald-800 dark:text-emerald-400">
                        <i data-lucide="pen-tool" class="w-5 h-5"></i>
                        <h3 class="font-display font-bold text-lg">${ws.title}</h3>
                    </div>
                    <p class="text-sm text-slate-700 dark:text-slate-300">${ws.instruction}</p>
                    
                    <div class="overflow-x-auto rounded-xl border border-emerald-200 dark:border-slate-700 bg-white dark:bg-slate-900">
                        <table class="w-full text-left text-xs sm:text-sm">
                            <thead>
                                <tr class="bg-emerald-700 text-white">
                                    <th class="py-2.5 px-4">${ws.tableHeaders[0]}</th>
                                    <th class="py-2.5 px-4">${ws.tableHeaders[1]}</th>
                                </tr>
                            </thead>
                            <tbody>${rows}</tbody>
                        </table>
                    </div>

                    <div class="space-y-2">
                        <label class="block text-xs font-bold uppercase tracking-wider text-slate-600 dark:text-slate-400">Draf Paragraf Deskripsimu:</label>
                        <textarea id="lho-draft-input" rows="3" placeholder="Tuliskan paragraf deskripsi bagian berdasarkan tabel data di atas..." class="w-full p-3.5 rounded-xl bg-white dark:bg-slate-900 border border-slate-300 dark:border-slate-700 text-sm focus:ring-2 focus:ring-emerald-600 focus:outline-none"></textarea>
                    </div>

                    <div class="flex flex-wrap items-center gap-3">
                        <button onclick="document.getElementById('lho-ideal-box').classList.toggle('hidden')" class="px-4 py-2.5 rounded-xl bg-emerald-700 hover:bg-emerald-600 text-white text-xs sm:text-sm font-bold transition flex items-center gap-2">
                            <i data-lucide="sparkles" class="w-4 h-4"></i>
                            <span>Bandingkan dengan Contoh Jawaban Ideal</span>
                        </button>
                    </div>

                    <div id="lho-ideal-box" class="hidden p-4 rounded-xl bg-white dark:bg-slate-900 border border-emerald-300 dark:border-emerald-700 space-y-1.5 fade-in">
                        <div class="text-xs font-bold text-emerald-700 dark:text-emerald-400">CONTOH PARAGRAF DESKRIPSI IDEAL:</div>
                        <p class="text-sm text-slate-800 dark:text-slate-200 leading-relaxed">${ws.idealAnswer}</p>
                    </div>
                </div>`;
            }

            container.innerHTML = `
                <div class="bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200 dark:border-slate-800 shadow-xs space-y-6">
                    <!-- Header Materi -->
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 pb-5 border-b border-slate-200 dark:border-slate-800">
                        <div>
                            <h2 class="font-display text-xl sm:text-2xl font-extrabold text-slate-900 dark:text-white">${data.title}</h2>
                            <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">${data.subtitle}</p>
                        </div>
                        <button onclick="toggleTopicComplete('${topicId}')" class="shrink-0 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold transition flex items-center gap-2 ${isCompleted ? 'bg-emerald-100 text-emerald-800 dark:bg-emerald-950 dark:text-emerald-300 border border-emerald-300 dark:border-emerald-800' : 'bg-slate-100 hover:bg-slate-200 dark:bg-slate-800 dark:hover:bg-slate-700 text-slate-700 dark:text-slate-200'}">
                            <i data-lucide="${isCompleted ? 'check-circle-2' : 'circle'}" class="w-4 h-4"></i>
                            <span>${isCompleted ? 'Sudah Dikuasai' : 'Tandai Sudah Paham'}</span>
                        </button>
                    </div>

                    <!-- Grid Struktur & Kaidah -->
                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                        <div class="lg:col-span-7 space-y-3">
                            <h3 class="font-display font-bold text-base flex items-center gap-2 text-slate-800 dark:text-slate-100">
                                <i data-lucide="layout-list" class="w-5 h-5 text-sman4-600 dark:text-emas-400"></i>
                                <span>${topicId === 'hikayat' ? 'Ciri, Unsur, Nilai & Penerapan STEM' : 'Struktur & Cara Mengidentifikasi'}</span>
                            </h3>
                            <div class="space-y-3">${structuresHTML}</div>
                        </div>

                        <div class="lg:col-span-5 space-y-3">
                            <h3 class="font-display font-bold text-base flex items-center gap-2 text-slate-800 dark:text-slate-100">
                                <i data-lucide="languages" class="w-5 h-5 text-sman4-600 dark:text-emas-400"></i>
                                <span>Kaidah Kebahasaan</span>
                            </h3>
                            <div class="space-y-2.5">${kaidahHTML}</div>
                        </div>
                    </div>

                    ${workshopHTML}
                </div>
            `;
            lucide.createIcons();
        }

        // ==========================================
        // 8. TAB 2: BANK CONTOH TEKS LENGKAP
        // ==========================================
        function filterTexts(category) {
            appState.currentTextFilter = category;
            document.querySelectorAll('.text-filter-btn').forEach(btn => {
                if (btn.getAttribute('data-filter') === category) {
                    btn.className = 'text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-sman4-800 text-white';
                } else {
                    btn.className = 'text-filter-btn px-3.5 py-2 rounded-xl text-xs font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200';
                }
            });
            renderTextsList();
        }

        function toggleTextAnalysis(textId) {
            const tags = document.querySelectorAll(`.analysis-tag-${textId}`);
            const note = document.getElementById(`analysis-note-${textId}`);
            const btn = document.getElementById(`analysis-btn-${textId}`);
            
            const isHidden = note.classList.contains('hidden');
            tags.forEach(t => t.classList.toggle('hidden'));
            note.classList.toggle('hidden');
            
            if (isHidden) {
                btn.innerHTML = `<i data-lucide="eye-off" class="w-4 h-4"></i><span>Sembunyikan Bedah Struktur</span>`;
                btn.classList.replace('bg-sman4-800', 'bg-amber-500');
                btn.classList.replace('text-white', 'text-slate-950');
            } else {
                btn.innerHTML = `<i data-lucide="scan-search" class="w-4 h-4"></i><span>Tampilkan Bedah Struktur & Kaidah</span>`;
                btn.classList.replace('bg-amber-500', 'bg-sman4-800');
                btn.classList.replace('text-slate-950', 'text-white');
            }
            lucide.createIcons();
        }

        function renderTextsList() {
            const container = document.getElementById('texts-list-container');
            const filtered = appState.currentTextFilter === 'all' 
                ? SAMPLE_TEXTS 
                : SAMPLE_TEXTS.filter(t => t.category === appState.currentTextFilter);

            container.innerHTML = filtered.map(item => {
                const segmentsHTML = item.segments.map(seg => `
                    <p class="leading-relaxed text-sm sm:text-base text-slate-700 dark:text-slate-300 whitespace-pre-line">
                        <span class="analysis-tag-${item.id} hidden hl-tag ${seg.tagColor}">${seg.tag}</span>${seg.text}
                    </p>
                `).join('');

                return `
                <article class="p-5 sm:p-6 rounded-2xl border border-slate-200 dark:border-slate-800 bg-slate-50/50 dark:bg-slate-800/30 space-y-4">
                    <div class="flex flex-wrap items-center justify-between gap-2">
                        <span class="px-3 py-1 rounded-full bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-indigo-300 text-xs font-bold">${item.categoryLabel}</span>
                        <button id="analysis-btn-${item.id}" onclick="toggleTextAnalysis('${item.id}')" class="px-3.5 py-2 rounded-xl bg-sman4-800 text-white text-xs font-bold transition flex items-center gap-1.5 shadow-xs">
                            <i data-lucide="scan-search" class="w-4 h-4"></i>
                            <span>Tampilkan Bedah Struktur & Kaidah</span>
                        </button>
                    </div>
                    <h3 class="font-display text-lg font-bold text-slate-900 dark:text-white">${item.title}</h3>
                    <div class="space-y-3 bg-white dark:bg-slate-900 p-4 sm:p-5 rounded-xl border border-slate-200/70 dark:border-slate-800">
                        ${segmentsHTML}
                    </div>
                    <div id="analysis-note-${item.id}" class="hidden p-4 rounded-xl bg-amber-50 dark:bg-amber-950/40 border border-amber-200 dark:border-amber-800/60 text-xs sm:text-sm text-amber-900 dark:text-amber-200 leading-relaxed fade-in">
                        <strong>Catatan Analisis Ujian:</strong> ${item.analysisNote}
                    </div>
                </article>`;
            }).join('');
            lucide.createIcons();
        }

        // ==========================================
        // 9. TAB 3: LATIHAN SOAL KUSTOM (QUIZ ENGINE)
        // ==========================================
        function startQuiz() {
            const selectedTopic = document.querySelector('input[name="quiz-topic"]:checked').value;
            const desiredCount = parseInt(document.querySelector('input[name="quiz-count"]:checked').value, 10);
            const useTimer = document.getElementById('quiz-timer-toggle').checked;

            let pool = selectedTopic === 'all' 
                ? [...QUIZ_BANK] 
                : QUIZ_BANK.filter(q => q.topic === selectedTopic);

            // Shuffle pool
            pool.sort(() => Math.random() - 0.5);

            // If desiredCount > pool.length (e.g., 20 questions on single topic), cycle cleanly so user always gets requested count
            let finalQuestions = [];
            while (finalQuestions.length < desiredCount) {
                for (let q of pool) {
                    if (finalQuestions.length < desiredCount) {
                        finalQuestions.push(q);
                    }
                }
            }

            appState.quizQuestions = finalQuestions;
            appState.quizAnswers = {};
            appState.quizCurrentIdx = 0;

            document.getElementById('quiz-setup-screen').classList.add('hidden');
            document.getElementById('quiz-result-screen').classList.add('hidden');
            document.getElementById('quiz-active-screen').classList.remove('hidden');

            // Setup Timer
            clearInterval(appState.quizTimerInterval);
            const timerDisplay = document.getElementById('quiz-timer-display');
            if (useTimer) {
                appState.quizSecondsLeft = desiredCount * 60;
                timerDisplay.classList.remove('hidden');
                timerDisplay.classList.add('flex');
                updateTimerText();
                appState.quizTimerInterval = setInterval(() => {
                    appState.quizSecondsLeft--;
                    updateTimerText();
                    if (appState.quizSecondsLeft <= 0) {
                        clearInterval(appState.quizTimerInterval);
                        showToast('Waktu habis! Jawaban otomatis dikumpulkan.', 'warning');
                        finishQuiz();
                    }
                }, 1000);
            } else {
                timerDisplay.classList.add('hidden');
                timerDisplay.classList.remove('flex');
            }

            renderQuizQuestion();
        }

        function updateTimerText() {
            const mins = Math.floor(appState.quizSecondsLeft / 60);
            const secs = appState.quizSecondsLeft % 60;
            document.getElementById('quiz-timer-text').textContent = 
                `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
        }

        function renderQuizQuestion() {
            const idx = appState.quizCurrentIdx;
            const total = appState.quizQuestions.length;
            const q = appState.quizQuestions[idx];

            document.getElementById('quiz-progress-badge').textContent = `Soal ${idx + 1} / ${total}`;
            document.getElementById('quiz-category-badge').textContent = q.topicLabel;
            document.getElementById('quiz-bar').style.width = `${((idx + 1) / total) * 100}%`;

            const passageEl = document.getElementById('quiz-passage');
            if (q.passage) {
                passageEl.textContent = q.passage;
                passageEl.classList.remove('hidden');
            } else {
                passageEl.classList.add('hidden');
            }

            document.getElementById('quiz-question-text').textContent = q.question;

            const letters = ['A', 'B', 'C', 'D', 'E'];
            const optionsContainer = document.getElementById('quiz-options-container');
            optionsContainer.innerHTML = q.options.map((opt, optIdx) => {
                const isSelected = appState.quizAnswers[idx] === optIdx;
                return `
                <button onclick="selectQuizOption(${optIdx})" class="w-full text-left p-4 rounded-xl border-2 transition flex items-start gap-3 ${isSelected ? 'border-sman4-600 bg-sman4-50 dark:bg-indigo-950/50 text-sman4-900 dark:text-white font-semibold' : 'border-slate-200 dark:border-slate-700 hover:border-slate-300 dark:hover:border-slate-600'}">
                    <span class="w-7 h-7 rounded-lg flex items-center justify-center text-xs font-bold shrink-0 ${isSelected ? 'bg-sman4-800 text-white' : 'bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300'}">${letters[optIdx]}</span>
                    <span class="text-sm leading-relaxed pt-0.5">${opt}</span>
                </button>`;
            }).join('');

            document.getElementById('quiz-prev-btn').disabled = idx === 0;
            const nextBtn = document.getElementById('quiz-next-btn');
            nextBtn.textContent = idx === total - 1 ? 'Selesai & Lihat Nilai' : 'Selanjutnya';
        }

        function selectQuizOption(optIdx) {
            appState.quizAnswers[appState.quizCurrentIdx] = optIdx;
            renderQuizQuestion();
        }

        function prevQuestion() {
            if (appState.quizCurrentIdx > 0) {
                appState.quizCurrentIdx--;
                renderQuizQuestion();
            }
        }

        function nextQuestion() {
            const total = appState.quizQuestions.length;
            if (appState.quizCurrentIdx < total - 1) {
                appState.quizCurrentIdx++;
                renderQuizQuestion();
            } else {
                finishQuiz();
            }
        }

        function quitQuiz() {
            clearInterval(appState.quizTimerInterval);
            resetQuizUI();
        }

        function resetQuizUI() {
            document.getElementById('quiz-active-screen').classList.add('hidden');
            document.getElementById('quiz-result-screen').classList.add('hidden');
            document.getElementById('quiz-setup-screen').classList.remove('hidden');
        }

        function finishQuiz() {
            clearInterval(appState.quizTimerInterval);
            const total = appState.quizQuestions.length;
            let correct = 0;
            const letters = ['A', 'B', 'C', 'D', 'E'];

            const reviewHTML = appState.quizQuestions.map((q, idx) => {
                const userAns = appState.quizAnswers[idx];
                const isCorrect = userAns === q.answer;
                if (isCorrect) correct++;

                return `
                <div class="p-4 rounded-xl border ${isCorrect ? 'border-emerald-200 dark:border-emerald-800/60 bg-emerald-50/40 dark:bg-emerald-950/20' : 'border-rose-200 dark:border-rose-800/60 bg-rose-50/40 dark:bg-rose-950/20'} space-y-2">
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold ${isCorrect ? 'text-emerald-700 dark:text-emerald-400' : 'text-rose-700 dark:text-rose-400'}">
                            Nomor ${idx + 1} • ${isCorrect ? 'BENAR' : 'KURANG TEPAT'}
                        </span>
                        <span class="text-xs text-slate-400">${q.topicLabel}</span>
                    </div>
                    <p class="text-sm font-semibold text-slate-900 dark:text-white">${q.question}</p>
                    <div class="text-xs space-y-1">
                        <div>Jawabanmu: <strong class="${isCorrect ? 'text-emerald-700 dark:text-emerald-400' : 'text-rose-600 dark:text-rose-400'}">${userAns !== undefined ? `${letters[userAns]}. ${q.options[userAns]}` : 'Tidak dijawab'}</strong></div>
                        ${!isCorrect ? `<div>Kunci Jawaban: <strong class="text-emerald-700 dark:text-emerald-400">${letters[q.answer]}. ${q.options[q.answer]}</strong></div>` : ''}
                    </div>
                    <div class="p-3 rounded-lg bg-white dark:bg-slate-900 text-xs text-slate-600 dark:text-slate-300 border border-slate-200/70 dark:border-slate-800">
                        <strong>Pembahasan:</strong> ${q.explanation}
                    </div>
                </div>`;
            }).join('');

            const score = Math.round((correct / total) * 100);
            if (appState.bestQuizScore === null || score > Number(appState.bestQuizScore)) {
                appState.bestQuizScore = score;
                saveState();
            }

            document.getElementById('quiz-final-score').textContent = score;
            document.getElementById('quiz-correct-count').textContent = correct;
            document.getElementById('quiz-wrong-count').textContent = total - correct;
            document.getElementById('quiz-total-count').textContent = total;
            document.getElementById('quiz-review-list').innerHTML = reviewHTML;

            document.getElementById('quiz-active-screen').classList.add('hidden');
            document.getElementById('quiz-result-screen').classList.remove('hidden');
            lucide.createIcons();
        }

        // ==========================================
        // 10. TAB 4: FLASHCARD 3D & ACTIVE RECALL
        // ==========================================
        function switchRecallMode(mode) {
            const btnFc = document.getElementById('btn-mode-fc');
            const btnAr = document.getElementById('btn-mode-ar');
            const viewFc = document.getElementById('recall-flashcard-view');
            const viewAr = document.getElementById('recall-active-view');

            if (mode === 'flashcard') {
                btnFc.className = 'px-4 py-2.5 rounded-xl text-sm font-bold bg-sman4-800 text-white flex items-center gap-2';
                btnAr.className = 'px-4 py-2.5 rounded-xl text-sm font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 flex items-center gap-2';
                viewFc.classList.remove('hidden');
                viewAr.classList.add('hidden');
            } else {
                btnAr.className = 'px-4 py-2.5 rounded-xl text-sm font-bold bg-sman4-800 text-white flex items-center gap-2';
                btnFc.className = 'px-4 py-2.5 rounded-xl text-sm font-bold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 flex items-center gap-2';
                viewAr.classList.remove('hidden');
                viewFc.classList.add('hidden');
                renderActiveRecall();
            }
        }

        function filterRecallItems() {
            const val = document.getElementById('recall-topic-filter').value;
            appState.filteredFC = val === 'all' 
                ? [...FLASHCARDS_DATA] 
                : FLASHCARDS_DATA.filter(c => c.topic === val);
            appState.currentFCIndex = 0;
            appState.isFCFlipped = false;
            document.getElementById('flashcard-inner').classList.remove('rotate-y-180');
            renderFlashcard();
        }

        function renderFlashcard() {
            const list = appState.filteredFC;
            const card = list[appState.currentFCIndex];
            const isMastered = appState.masteredFlashcards.includes(card.id);

            document.getElementById('fc-counter').textContent = `Kartu ${appState.currentFCIndex + 1} dari ${list.length}`;
            const statusBadge = document.getElementById('fc-status-badge');
            if (isMastered) {
                statusBadge.textContent = 'Sudah Hafal ✓';
                statusBadge.className = 'px-2.5 py-1 rounded-full bg-emerald-100 dark:bg-emerald-950 text-emerald-700 dark:text-emerald-300 font-bold';
            } else {
                statusBadge.textContent = 'Perlu Diulang';
                statusBadge.className = 'px-2.5 py-1 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-700 dark:text-slate-300';
            }

            document.getElementById('fc-front-tag').textContent = card.tag;
            document.getElementById('fc-front-text').textContent = card.front;
            document.getElementById('fc-back-text').innerHTML = card.back.replace(/\n/g, '<br>');
        }

        function flipFlashcard() {
            appState.isFCFlipped = !appState.isFCFlipped;
            const inner = document.getElementById('flashcard-inner');
            if (appState.isFCFlipped) {
                inner.classList.add('rotate-y-180');
            } else {
                inner.classList.remove('rotate-y-180');
            }
        }

        function nextFlashcard() {
            appState.isFCFlipped = false;
            document.getElementById('flashcard-inner').classList.remove('rotate-y-180');
            appState.currentFCIndex = (appState.currentFCIndex + 1) % appState.filteredFC.length;
            setTimeout(renderFlashcard, 120);
        }

        function prevFlashcard() {
            appState.isFCFlipped = false;
            document.getElementById('flashcard-inner').classList.remove('rotate-y-180');
            appState.currentFCIndex = (appState.currentFCIndex - 1 + appState.filteredFC.length) % appState.filteredFC.length;
            setTimeout(renderFlashcard, 120);
        }

        function markFlashcard(mastered) {
            const card = appState.filteredFC[appState.currentFCIndex];
            const idx = appState.masteredFlashcards.indexOf(card.id);
            if (mastered && idx === -1) {
                appState.masteredFlashcards.push(card.id);
                showToast('Mantap! Kartu ditandai sudah hafal.', 'success');
            } else if (!mastered && idx !== -1) {
                appState.masteredFlashcards.splice(idx, 1);
                showToast('Kartu ditandai untuk diulang kembali.', 'info');
            }
            saveState();
            nextFlashcard();
        }

        // Active Recall Mode
        function renderActiveRecall() {
            const item = ACTIVE_RECALL_PROMPTS[appState.currentARIndex];
            document.getElementById('ar-tag').textContent = item.tag;
            document.getElementById('ar-counter').textContent = `Pertanyaan ${appState.currentARIndex + 1} / ${ACTIVE_RECALL_PROMPTS.length}`;
            document.getElementById('ar-prompt').textContent = item.prompt;
            document.getElementById('ar-user-input').value = '';
            document.getElementById('ar-answer-box').classList.add('hidden');
            document.getElementById('ar-ideal-answer').innerHTML = item.answer.replace(/\n/g, '<br>');
        }

        function revealActiveRecall() {
            document.getElementById('ar-answer-box').classList.remove('hidden');
        }

        function nextActiveRecall() {
            appState.currentARIndex = (appState.currentARIndex + 1) % ACTIVE_RECALL_PROMPTS.length;
            renderActiveRecall();
        }

        // ==========================================
        // 11. TAB 5: TANYA AI TUTOR (GEMINI API)
        // ==========================================
        function sendQuickPrompt(text) {
            document.getElementById('chat-input').value = text;
            handleChatSubmit(new Event('submit'));
        }

        function clearChat() {
            const box = document.getElementById('chat-messages');
            box.innerHTML = `
                <div class="flex gap-3 max-w-2xl">
                    <div class="w-8 h-8 rounded-lg bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-emas-400 flex items-center justify-center shrink-0 mt-1">
                        <i data-lucide="sparkles" class="w-4 h-4"></i>
                    </div>
                    <div class="bg-slate-100 dark:bg-slate-800 p-4 rounded-2xl rounded-tl-none text-sm leading-relaxed text-slate-800 dark:text-slate-200">
                        Percakapan direset. Silakan ajukan pertanyaan baru seputar materi Bahasa Indonesia Kelas X!
                    </div>
                </div>`;
            lucide.createIcons();
        }

        async function handleChatSubmit(e) {
            e.preventDefault();
            const inputEl = document.getElementById('chat-input');
            const sendBtn = document.getElementById('chat-send-btn');
            const userText = inputEl.value.trim();
            if (!userText) return;

            inputEl.value = '';
            appendMessage('user', userText);

            const loadingId = 'loading-' + Date.now();
            appendLoading(loadingId);
            sendBtn.disabled = true;

            try {
                const reply = await fetchGeminiTutor(userText);
                document.getElementById(loadingId)?.remove();
                appendMessage('ai', reply);
            } catch (err) {
                document.getElementById(loadingId)?.remove();
                // Fallback smart local tutor response if offline/API unreachable
                const fallbackReply = generateOfflineTutorFallback(userText);
                appendMessage('ai', fallbackReply);
            } finally {
                sendBtn.disabled = false;
            }
        }

        function appendMessage(role, text) {
            const box = document.getElementById('chat-messages');
            const wrapper = document.createElement('div');
            
            // Format simple markdown bold & newlines cleanly
            const formatted = text
                .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
                .replace(/\n/g, '<br>');

            if (role === 'user') {
                wrapper.className = 'flex justify-end fade-in';
                wrapper.innerHTML = `
                    <div class="bg-sman4-800 text-white p-3.5 sm:p-4 rounded-2xl rounded-tr-none max-w-xl text-sm leading-relaxed shadow-xs">
                        ${formatted}
                    </div>`;
            } else {
                wrapper.className = 'flex gap-3 max-w-2xl fade-in';
                wrapper.innerHTML = `
                    <div class="w-8 h-8 rounded-lg bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-emas-400 flex items-center justify-center shrink-0 mt-1">
                        <i data-lucide="sparkles" class="w-4 h-4"></i>
                    </div>
                    <div class="bg-slate-100 dark:bg-slate-800 p-4 rounded-2xl rounded-tl-none text-sm leading-relaxed text-slate-800 dark:text-slate-200">
                        ${formatted}
                    </div>`;
            }
            box.appendChild(wrapper);
            box.scrollTop = box.scrollHeight;
            lucide.createIcons();
        }

        function appendLoading(id) {
            const box = document.getElementById('chat-messages');
            const wrapper = document.createElement('div');
            wrapper.id = id;
            wrapper.className = 'flex gap-3 max-w-2xl fade-in';
            wrapper.innerHTML = `
                <div class="w-8 h-8 rounded-lg bg-sman4-100 dark:bg-indigo-950 text-sman4-800 dark:text-emas-400 flex items-center justify-center shrink-0 mt-1">
                    <i data-lucide="loader-2" class="w-4 h-4 animate-spin"></i>
                </div>
                <div class="bg-slate-100 dark:bg-slate-800 px-4 py-3 rounded-2xl rounded-tl-none text-xs text-slate-500">
                    Kak AI Tutor sedang menyusun penjelasan...
                </div>`;
            box.appendChild(wrapper);
            box.scrollTop = box.scrollHeight;
            lucide.createIcons();
        }

        async function fetchGeminiTutor(userQuery) {
            const systemPrompt = "Kamu adalah Kak AI Tutor Bahasa Indonesia Kelas X yang ramah, suportif, dan cerdas khusus membantu siswa-siswi SMAN 4 Kendari mempersiapkan ulangan. Jelaskan konsep dengan bahasa yang jelas, terstruktur (gunakan poin-poin jika perlu), ringkas, dan berikan contoh konkret. Fokus pada materi Kurikulum Merdeka Kelas X: Teks LHO (struktur, kaidah, mengolah data jadi deskripsi), Teks Eksposisi (tesis, argumen, penegasan ulang), Teks Anekdot (abstraksi, orientasi, krisis, reaksi, koda, sindiran), dan Teks Hikayat (ciri, unsur intrinsik, nilai, dan integrasi dalam pembelajaran STEM).";
            const apiKey = ""; 
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                systemInstruction: { parts: [{ text: systemPrompt }] }
            };

            let delay = 1000;
            for (let attempt = 0; attempt < 3; attempt++) {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                if (response.ok) {
                    const result = await response.json();
                    const text = result.candidates?.[0]?.content?.parts?.[0]?.text;
                    if (text) return text;
                }
                await new Promise(res => setTimeout(res, delay));
                delay *= 2;
            }
            throw new Error('API request failed');
        }

        function generateOfflineTutorFallback(query) {
            const q = query.toLowerCase();
            if (q.includes('lho') || q.includes('definisi') || q.includes('deskripsi')) {
                return "**Penjelasan Ringkas Teks LHO:**\n1. **Kalimat Definisi** menjelaskan makna umum objek (menggunakan kata *adalah, merupakan, yaitu*). Contoh: *Teluk Kendari adalah perairan semi-tertutup di Sulawesi Tenggara.*\n2. **Kalimat Deskripsi** merinci sifat/ciri fisik objek secara objektif. Contoh: *Perairan ini dikelilingi ekosistem mangrove dengan kedalaman bervariasi.*";
            }
            if (q.includes('eksposisi') || q.includes('tesis')) {
                return "**Trik Mengidentifikasi Struktur Teks Eksposisi:**\n• **Tesis** (Paragraf 1): Cari kalimat pendapat/sikap utama penulis terhadap suatu isu.\n• **Argumentasi** (Paragraf Tengah): Cari bukti berupa data angka, kutipan ahli (*menurut..., berdasarkan...*), dan konjungsi sebab-akibat (*akibatnya, sehingga*).\n• **Penegasan Ulang** (Paragraf Akhir): Merangkum tesis kembali, biasanya diawali *oleh karena itu* atau *dengan demikian*.";
            }
            if (q.includes('hikayat') || q.includes('stem')) {
                return "**Integrasi Teks Hikayat dalam Pembelajaran STEM:**\nSelain memiliki ciri *kemustahilan, kesaktian, anonim, istana sentris,* dan *bahasa arkais*, hikayat dapat dianalisis secara STEM:\n• **Science:** Mengkaji khasiat tanaman obat herbal atau hukum fisika di balik peristiwa cerita.\n• **Technology:** Teknik penyaringan/ekstraksi ramuan atau membuat simulasi animasi.\n• **Engineering:** Rekayasa alat sederhana (tuas/katrol) yang digunakan tokoh cerdik.\n• **Mathematics:** Perhitungan logika pembagian, rasio, dan estimasi.";
            }
            return "Pertanyaan bagus! Untuk persiapan ulangan Bahasa Indonesia Kelas X di SMAN 4 Kendari, pastikan kamu menguasai:\n1. **Teks LHO**: Pernyataan Umum, Deskripsi Bagian (sesuai data tabel), Deskripsi Manfaat.\n2. **Teks Eksposisi**: Tesis, Argumentasi, Penegasan Ulang.\n3. **Teks Anekdot**: Abstraksi, Orientasi, Krisis (inti sindiran), Reaksi, Koda.\n4. **Teks Hikayat**: Ciri klasik, nilai luhur, dan analisis STEM.\n\nCoba ketik pertanyaan lebih spesifik tentang salah satu bab di atas ya!";
        }

        // ==========================================
        // 12. INITIALIZE DASHBOARD ON LOAD
        // ==========================================
        window.addEventListener('DOMContentLoaded', () => {
            updateProgressUI();
            renderTopicDetail('lho');
            renderTextsList();
            renderFlashcard();
            renderActiveRecall();
            lucide.createIcons();
        });
    </script>
</body>
</html>
