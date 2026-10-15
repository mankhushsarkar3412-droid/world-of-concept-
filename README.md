<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>World of Concept — Complete Education App</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
  <style>
    body { font-family: system-ui, -apple-system, sans-serif; background-color: #f1f5f9; user-select: none; -webkit-tap-highlight-color: transparent; }
    .hide-scroll::-webkit-scrollbar { display: none; }
    .hide-scroll { -ms-overflow-style: none; scrollbar-width: none; }
    .active-nav { color: #2563eb !important; font-weight: 700; }
    @keyframes pulse-live { 0%, 100% { opacity: 1; } 50% { opacity: 0.4; } }
    .live-dot { animation: pulse-live 1.5s infinite; }
  </style>
</head>
<body class="max-w-md mx-auto bg-slate-50 min-h-screen pb-20 shadow-xl relative overflow-x-hidden">

  <!-- ================= HEADER (Sticky Top) ================= -->
  <header class="sticky top-0 z-40 bg-white border-b border-slate-200 px-3 py-2.5 shadow-sm">
    <div class="flex items-center justify-between">
      <!-- Left: Logo & App Name -->
      <div class="flex items-center gap-2 cursor-pointer" onclick="switchTab('home')">
        <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-blue-700 to-indigo-500 flex items-center justify-center text-white font-black text-lg shadow">
          W
        </div>
        <div>
          <h1 class="font-extrabold text-slate-800 text-sm leading-tight tracking-tight">WORLD OF CONCEPT</h1>
          <!-- Board & Class Selector right near header -->
          <button onclick="openBoardModal()" class="flex items-center gap-1 text-[11px] font-semibold text-blue-600 bg-blue-50 px-2 py-0.5 rounded-full mt-0.5">
            <span id="headerBoardClass">Bihar Board · Class 10</span>
            <i class="fa-solid fa-chevron-down text-[9px]"></i>
          </button>
        </div>
      </div>

      <!-- Right: Search, Notification, 3-dot Menu, Profile Avatar -->
      <div class="flex items-center gap-1.5">
        <button onclick="toggleSearchModal()" class="w-8 h-8 rounded-full bg-slate-100 flex items-center justify-center text-slate-600 hover:bg-slate-200">
          <i class="fa-solid fa-magnifying-glass text-xs"></i>
        </button>
        <button onclick="openNotifModal()" class="w-8 h-8 rounded-full bg-slate-100 flex items-center justify-center text-slate-600 relative hover:bg-slate-200">
          <i class="fa-solid fa-bell text-xs"></i>
          <span class="w-2 h-2 rounded-full bg-red-500 absolute top-1.5 right-1.5"></span>
        </button>
        <button onclick="toggleThreeDotMenu()" class="w-8 h-8 rounded-full bg-slate-100 flex items-center justify-center text-slate-600 hover:bg-slate-200">
          <i class="fa-solid fa-ellipsis-vertical text-xs"></i>
        </button>
        <button onclick="switchTab('profile')" class="ml-0.5">
          <img id="headerAvatar" src="https://api.dicebear.com/7.x/avataaars/svg?seed=Aman" alt="Profile" class="w-8 h-8 rounded-full border-2 border-blue-600 bg-blue-50">
        </button>
      </div>
    </div>

    <!-- 3-Dot Dropdown Menu -->
    <div id="threeDotMenu" class="hidden absolute right-3 top-14 bg-white rounded-xl shadow-xl border border-slate-200 w-48 py-1.5 z-50 text-xs font-medium text-slate-700">
      <button onclick="switchTab('my-courses'); toggleThreeDotMenu();" class="w-full text-left px-4 py-2 hover:bg-slate-50 flex items-center gap-2">
        <i class="fa-solid fa-book-open text-blue-600"></i> My Enrolled Courses
      </button>
      <button onclick="openAdminGate(); toggleThreeDotMenu();" class="w-full text-left px-4 py-2 hover:bg-slate-50 flex items-center gap-2 text-indigo-700 font-bold">
        <i class="fa-solid fa-user-shield"></i> Admin Panel (प्रिंसिपल)
      </button>
      <button onclick="openLoginModal(); toggleThreeDotMenu();" class="w-full text-left px-4 py-2 hover:bg-slate-50 flex items-center gap-2 border-t border-slate-100">
        <i class="fa-solid fa-right-to-bracket text-emerald-600"></i> Login / Switch Account
      </button>
    </div>
  </header>

  <!-- ================= MAIN CONTENT CONTAINER ================= -->
  <main class="p-3 space-y-4">

    <!-- ==================== 1. HOME PAGE ==================== -->
    <section id="page-home" class="space-y-4">
      <!-- Student Profile Summary Card -->
      <div class="bg-gradient-to-r from-blue-700 via-indigo-700 to-slate-900 rounded-2xl p-3.5 text-white shadow-md">
        <div class="flex items-center justify-between">
          <div class="flex items-center gap-3">
            <img id="homeCardAvatar" src="https://api.dicebear.com/7.x/avataaars/svg?seed=Aman" class="w-12 h-12 rounded-full border-2 border-amber-400 bg-white p-0.5" alt="Student">
            <div>
              <div class="flex items-center gap-1.5">
                <h2 id="homeStudentName" class="font-bold text-sm">अमन कुमार (Student)</h2>
                <span id="roleBadge" class="text-[10px] bg-amber-400 text-slate-900 font-extrabold px-1.5 py-0.5 rounded">PRO</span>
              </div>
              <p id="homeBoardClassText" class="text-xs text-blue-200">Bihar Board · Class 10</p>
              <p id="homeGoalText" class="text-[11px] text-amber-300 font-medium mt-0.5">🎯 लक्ष्य: बोर्ड परीक्षा में 95%+ अंक</p>
            </div>
          </div>
          <div class="text-right bg-white/10 px-2.5 py-1.5 rounded-xl backdrop-blur-sm">
            <p class="text-[10px] text-blue-200">कुल स्कोर</p>
            <p id="homeScoreText" class="text-base font-black text-amber-400">840 XP</p>
          </div>
        </div>
        <!-- Study Progress Bar -->
        <div class="mt-3">
          <div class="flex justify-between text-[11px] mb-1">
            <span class="text-blue-100">पढ़ाई की प्रगति (Overall Progress)</span>
            <span id="homeProgressPercent" class="font-bold text-amber-300">68%</span>
          </div>
          <div class="w-full h-2 bg-white/20 rounded-full overflow-hidden">
            <div id="homeProgressBar" class="h-full bg-amber-400 rounded-full transition-all duration-300" style="width: 68%;"></div>
          </div>
        </div>
      </div>

      <!-- 3 Shortcuts in One Single Line: 1. My Courses, 2. Live, 3. Daily Study Plan -->
      <div class="grid grid-cols-3 gap-2.5">
        <!-- 1. My Courses -->
        <button onclick="switchTab('my-courses')" class="bg-white p-3 rounded-2xl border border-slate-200 shadow-sm flex flex-col items-center justify-center gap-1.5 active:scale-95 transition">
          <div class="w-10 h-10 rounded-xl bg-blue-50 text-blue-600 flex items-center justify-center text-lg">
            <i class="fa-solid fa-graduation-cap"></i>
          </div>
          <span class="text-xs font-bold text-slate-800 leading-tight text-center">My Courses</span>
        </button>

        <!-- 2. Live (Protected Section - Unchanged Design & Role) -->
        <button onclick="openLiveSection()" class="bg-white p-3 rounded-2xl border border-red-200 shadow-sm flex flex-col items-center justify-center gap-1.5 relative active:scale-95 transition">
          <span class="absolute top-1.5 right-2 flex items-center gap-1 text-[9px] font-extrabold text-red-600 bg-red-50 px-1.5 py-0.5 rounded-full">
            <span class="w-1.5 h-1.5 rounded-full bg-red-600 live-dot"></span> LIVE
          </span>
          <div class="w-10 h-10 rounded-xl bg-red-50 text-red-600 flex items-center justify-center text-lg">
            <i class="fa-solid fa-tower-broadcast"></i>
          </div>
          <span class="text-xs font-bold text-slate-800 leading-tight text-center">Live</span>
        </button>

        <!-- 3. Daily Study Plan -->
        <button onclick="switchTab('daily-plan')" class="bg-white p-3 rounded-2xl border border-slate-200 shadow-sm flex flex-col items-center justify-center gap-1.5 active:scale-95 transition">
          <div class="w-10 h-10 rounded-xl bg-emerald-50 text-emerald-600 flex items-center justify-center text-lg">
            <i class="fa-solid fa-calendar-check"></i>
          </div>
          <span class="text-xs font-bold text-slate-800 leading-tight text-center">Daily Study Plan</span>
        </button>
      </div>

      <!-- Recently Viewed Section (Working Resume Feature) -->
      <div class="bg-white p-3.5 rounded-2xl border border-slate-200 shadow-sm">
        <div class="flex items-center justify-between mb-2.5">
          <h3 class="font-extrabold text-slate-800 text-xs flex items-center gap-1.5">
            <i class="fa-solid fa-clock-rotate-left text-blue-600"></i> Recently Viewed (जहाँ छोड़ा था वहीं से पढ़ें)
          </h3>
          <span class="text-[10px] text-slate-400">Auto-Saved</span>
        </div>
        <div id="recentlyViewedList" class="space-y-2">
          <!-- Populated dynamically by JS -->
        </div>
      </div>

      <!-- Top Teachers Section -->
      <div class="bg-white p-3.5 rounded-2xl border border-slate-200 shadow-sm">
        <h3 class="font-extrabold text-slate-800 text-xs flex items-center gap-1.5 mb-3">
          <i class="fa-solid fa-chalkboard-user text-indigo-600"></i> Top Teachers (हमारे विशेषज्ञ शिक्षक)
        </h3>
        <div class="grid grid-cols-3 gap-2 text-center" id="topTeachersList">
          <div class="bg-slate-50 p-2.5 rounded-xl border border-slate-100">
            <img src="https://api.dicebear.com/7.x/avataaars/svg?seed=RKPatel" class="w-11 h-11 mx-auto rounded-full bg-indigo-100 mb-1.5" alt="RK Patel Sir">
            <p class="font-bold text-slate-800 text-[11px]">RK Patel Sir</p>
            <p class="text-[10px] text-indigo-600 font-semibold">Physics & Concept</p>
            <p class="text-[9px] text-slate-500 mt-0.5">⭐ 4.9 (12k+ छात्र)</p>
          </div>
          <div class="bg-slate-50 p-2.5 rounded-xl border border-slate-100">
            <img src="https://api.dicebear.com/7.x/avataaars/svg?seed=SKVerma" class="w-11 h-11 mx-auto rounded-full bg-blue-100 mb-1.5" alt="S.K. Verma">
            <p class="font-bold text-slate-800 text-[11px]">S.K. Verma Sir</p>
            <p class="text-[10px] text-blue-600 font-semibold">Mathematics</p>
            <p class="text-[9px] text-slate-500 mt-0.5">⭐ 4.8 (9.5k+ छात्र)</p>
          </div>
          <div class="bg-slate-50 p-2.5 rounded-xl border border-slate-100">
            <img src="https://api.dicebear.com/7.x/avataaars/svg?seed=AnjaliMam" class="w-11 h-11 mx-auto rounded-full bg-emerald-100 mb-1.5" alt="Anjali Mam">
            <p class="font-bold text-slate-800 text-[11px]">Anjali Ma'am</p>
            <p class="text-[10px] text-emerald-600 font-semibold">Biology & Chem</p>
            <p class="text-[9px] text-slate-500 mt-0.5">⭐ 4.9 (10k+ छात्र)</p>
          </div>
        </div>
      </div>

      <!-- Topper's Corner (Verified Data Driven) -->
      <div class="bg-gradient-to-br from-amber-50 to-orange-50 p-3.5 rounded-2xl border border-amber-200 shadow-sm">
        <div class="flex items-center justify-between mb-2.5">
          <h3 class="font-extrabold text-amber-900 text-xs flex items-center gap-1.5">
            <i class="fa-solid fa-trophy text-amber-500"></i> Topper’s Corner (सत्यापित टेस्ट स्कोर)
          </h3>
          <span class="text-[10px] bg-amber-200 text-amber-900 px-2 py-0.5 rounded-full font-bold">Real Test Data</span>
        </div>
        <div id="toppersList" class="space-y-2">
          <!-- Populated from actual test records -->
        </div>
      </div>
    </section>

    <!-- ==================== 2. MY COURSES PAGE (Separate from All Courses) ==================== -->
    <section id="page-my-courses" class="hidden space-y-3">
      <div class="flex items-center justify-between bg-white p-3 rounded-2xl border border-slate-200">
        <div>
          <h2 class="font-extrabold text-slate-800 text-sm">🎒 My Enrolled Courses</h2>
          <p class="text-[11px] text-slate-500">सिर्फ़ आपके द्वारा चुने गए कोर्स यहाँ दिखते हैं</p>
        </div>
        <button onclick="switchTab('all-courses')" class="text-xs font-bold text-blue-600 bg-blue-50 px-3 py-1.5 rounded-xl">
          + नया कोर्स जोड़ें
        </button>
      </div>
      <div id="myCoursesContainer" class="space-y-2.5"></div>
    </section>

    <!-- ==================== 3. SINGLE COURSE DETAILS PAGE ==================== -->
    <section id="page-course-detail" class="hidden space-y-3">
      <button onclick="switchTab('my-courses')" class="text-xs font-bold text-slate-600 flex items-center gap-1.5 bg-white px-3 py-1.5 rounded-xl border border-slate-200">
        <i class="fa-solid fa-arrow-left"></i> वापस जाएं
      </button>
      <div id="courseDetailContent" class="space-y-3"></div>
    </section>

    <!-- ==================== 4. ALL COURSES PAGE (With Working Filters) ==================== -->
    <section id="page-all-courses" class="hidden space-y-3">
      <div class="bg-white p-3.5 rounded-2xl border border-slate-200 space-y-3">
        <div>
          <h2 class="font-extrabold text-slate-800 text-sm">📚 All Available Courses</h2>
          <p class="text-[11px] text-slate-500">अपना बोर्ड और कक्षा चुनकर कोर्स फ़िल्टर करें</p>
        </div>

        <!-- Board Filter Pills -->
        <div>
          <p class="text-[10px] font-bold text-slate-400 uppercase mb-1.5">1. बोर्ड चुनें (Select Board):</p>
          <div class="flex gap-1.5 overflow-x-auto hide-scroll pb-1" id="boardFilterBar">
            <button onclick="setCourseFilter('board', 'ALL')" data-board="ALL" class="filter-board-btn text-xs px-3 py-1.5 rounded-xl font-bold bg-blue-600 text-white">All Boards</button>
            <button onclick="setCourseFilter('board', 'Bihar Board')" data-board="Bihar Board" class="filter-board-btn text-xs px-3 py-1.5 rounded-xl font-bold bg-slate-100 text-slate-700">Bihar Board</button>
            <button onclick="setCourseFilter('board', 'UP Board')" data-board="UP Board" class="filter-board-btn text-xs px-3 py-1.5 rounded-xl font-bold bg-slate-100 text-slate-700">UP Board</button>
            <button onclick="setCourseFilter('board', 'Other Boards')" data-board="Other Boards" class="filter-board-btn text-xs px-3 py-1.5 rounded-xl font-bold bg-slate-100 text-slate-700">Other Boards</button>
          </div>
        </div>

        <!-- Class Filter Pills -->
        <div>
          <p class="text-[10px] font-bold text-slate-400 uppercase mb-1.5">2. कक्षा चुनें (Select Class 9 - 12):</p>
          <div class="flex gap-1.5 overflow-x-auto hide-scroll pb-1" id="classFilterBar">
            <button onclick="setCourseFilter('class', 'ALL')" data-class="ALL" class="filter-class-btn text-xs px-3 py-1 rounded-xl font-bold bg-indigo-600 text-white">All Classes</button>
            <button onclick="setCourseFilter('class', 'Class 9')" data-class="Class 9" class="filter-class-btn text-xs px-3 py-1 rounded-xl font-bold bg-slate-100 text-slate-700">Class 9</button>
            <button onclick="setCourseFilter('class', 'Class 10')" data-class="Class 10" class="filter-class-btn text-xs px-3 py-1 rounded-xl font-bold bg-slate-100 text-slate-700">Class 10</button>
            <button onclick="setCourseFilter('class', 'Class 11')" data-class="Class 11" class="filter-class-btn text-xs px-3 py-1 rounded-xl font-bold bg-slate-100 text-slate-700">Class 11</button>
            <button onclick="setCourseFilter('class', 'Class 12')" data-class="Class 12" class="filter-class-btn text-xs px-3 py-1 rounded-xl font-bold bg-slate-100 text-slate-700">Class 12</button>
          </div>
        </div>
      </div>

      <!-- Filtered Course Results -->
      <div id="allCoursesList" class="space-y-2.5"></div>
    </section>

    <!-- ==================== 5. VIDEO PLAYER PAGE (3x Speed, Landscape, Persistent Chat) ==================== -->
    <section id="page-video-player" class="hidden space-y-3">
      <button onclick="closeVideoPlayer()" class="text-xs font-bold text-slate-600 flex items-center gap-1.5 bg-white px-3 py-1.5 rounded-xl border border-slate-200">
        <i class="fa-solid fa-arrow-left"></i> कोर्स पेज पर वापस जाएं
      </button>

      <!-- Video Container -->
      <div id="videoWrapper" class="bg-black rounded-2xl overflow-hidden shadow-lg relative">
        <video id="mainVideoElement" class="w-full aspect-video bg-black" playsinline controlsList="nodownload">
          <source id="mainVideoSource" src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" type="video/mp4">
        </video>

        <!-- Custom Smart Controls Bar -->
        <div class="bg-slate-900 text-white p-2.5 space-y-2">
          <!-- Progress Scrub Bar -->
          <div class="flex items-center gap-2 text-[11px]">
            <span id="vidCurrentTime">0:00</span>
            <input id="vidSeekBar" type="range" min="0" max="100" value="0" class="w-full accent-blue-500 h-1.5 bg-slate-700 rounded-lg cursor-pointer">
            <span id="vidDuration">0:00</span>
          </div>

          <!-- Control Buttons: Play/Pause, Speed up to 3x, Quality, Fullscreen Landscape -->
          <div class="flex items-center justify-between">
            <div class="flex items-center gap-3">
              <button onclick="togglePlayPause()" class="w-8 h-8 rounded-full bg-blue-600 flex items-center justify-center text-white">
                <i id="playPauseIcon" class="fa-solid fa-play text-xs"></i>
              </button>
              <button onclick="skipVideo(-10)" class="text-xs text-slate-300 hover:text-white"><i class="fa-solid fa-rotate-left"></i> 10s</button>
              <button onclick="skipVideo(10)" class="text-xs text-slate-300 hover:text-white">10s <i class="fa-solid fa-rotate-right"></i></button>
            </div>

            <div class="flex items-center gap-2">
              <!-- Playback Speed up to 3x -->
              <select id="vidSpeedSelect" onchange="changeVideoSpeed(this.value)" class="bg-slate-800 text-white text-[11px] font-bold px-2 py-1 rounded-lg border border-slate-700">
                <option value="0.5">0.5x</option>
                <option value="1" selected>1.0x (Normal)</option>
                <option value="1.5">1.5x</option>
                <option value="2">2.0x</option>
                <option value="2.5">2.5x</option>
                <option value="3">3.0x (Super Fast)</option>
              </select>

              <!-- Real Source Quality Selector -->
              <select id="vidQualitySelect" onchange="changeVideoQuality(this.value)" class="bg-slate-800 text-white text-[11px] font-bold px-2 py-1 rounded-lg border border-slate-700">
                <option value="Auto">Auto (Source)</option>
                <option value="720p">720p HD (Source)</option>
                <option value="360p">360p Data Saver</option>
              </select>

              <!-- Fullscreen + Landscape Lock Button -->
              <button onclick="enterLandscapeFullscreen()" class="bg-slate-800 px-2.5 py-1 rounded-lg text-xs border border-slate-700 hover:bg-slate-700" title="Fullscreen">
                <i class="fa-solid fa-expand"></i>
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Compact Video Info (Does not block video) -->
      <div class="bg-white p-3 rounded-2xl border border-slate-200 flex items-center justify-between">
        <div>
          <span id="playingChapterBadge" class="text-[10px] font-bold text-blue-600 bg-blue-50 px-2 py-0.5 rounded">Chapter 1</span>
          <h2 id="playingVideoTitle" class="font-bold text-slate-800 text-sm mt-0.5">प्रकाश का परावर्तन (Reflection of Light)</h2>
        </div>
        <button onclick="toggleVideoComments()" class="text-xs font-bold bg-indigo-50 text-indigo-700 px-3 py-1.5 rounded-xl">
          <i class="fa-solid fa-comments"></i> Doubts / Chat
        </button>
      </div
