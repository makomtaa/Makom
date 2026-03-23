<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MSIMBA DAY School System</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    
    .gradient-bg {
      background: linear-gradient(135deg, #1e3a5f 0%, #0d1b2a 50%, #1b263b 100%);
    }
    
    .card-gradient {
      background: linear-gradient(145deg, rgba(255,255,255,0.95) 0%, rgba(248,250,252,0.9) 100%);
      backdrop-filter: blur(10px);
    }
    
    .btn-primary {
      background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
      transition: all 0.3s ease;
    }
    
    .btn-primary:hover {
      background: linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%);
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(245, 158, 11, 0.3);
    }
    
    .btn-secondary {
      background: linear-gradient(135deg, #1e3a5f 0%, #0d1b2a 100%);
      transition: all 0.3s ease;
    }
    
    .btn-secondary:hover {
      background: linear-gradient(135deg, #2d4a6f 0%, #1e3a5f 100%);
      transform: translateY(-2px);
    }
    
    .input-styled {
      border: 2px solid #e5e7eb;
      transition: all 0.3s ease;
    }
    
    .input-styled:focus {
      border-color: #f59e0b;
      box-shadow: 0 0 0 4px rgba(245, 158, 11, 0.1);
    }
    
    .table-header {
      background: linear-gradient(135deg, #1e3a5f 0%, #0d1b2a 100%);
    }
    
    .notification-badge {
      animation: pulse 2s infinite;
    }
    
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    
    .fade-in {
      animation: fadeIn 0.5s ease-out;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .slide-in {
      animation: slideIn 0.4s ease-out;
    }
    
    @keyframes slideIn {
      from { opacity: 0; transform: translateX(-20px); }
      to { opacity: 1; transform: translateX(0); }
    }
    
    .grade-A { background: linear-gradient(135deg, #10b981, #059669); }
    .grade-B { background: linear-gradient(135deg, #3b82f6, #2563eb); }
    .grade-C { background: linear-gradient(135deg, #f59e0b, #d97706); }
    .grade-D { background: linear-gradient(135deg, #f97316, #ea580c); }
    .grade-F { background: linear-gradient(135deg, #ef4444, #dc2626); }
    
    .school-logo {
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 10px 30px rgba(245, 158, 11, 0.3);
    }
    
    .message-bubble {
      position: relative;
    }
    
    .message-bubble::before {
      content: '';
      position: absolute;
      bottom: -8px;
      left: 20px;
      border-width: 8px;
      border-style: solid;
      border-color: #e5e7eb transparent transparent transparent;
    }
    
    .message-sent::before {
      left: auto;
      right: 20px;
      border-color: #1e3a5f transparent transparent transparent;
    }
    
    ::-webkit-scrollbar {
      width: 8px;
    }
    
    ::-webkit-scrollbar-track {
      background: #f1f5f9;
      border-radius: 4px;
    }
    
    ::-webkit-scrollbar-thumb {
      background: linear-gradient(135deg, #1e3a5f, #0d1b2a);
      border-radius: 4px;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full gradient-bg">
  <div id="app" class="h-full w-full overflow-auto"><!-- Portal Selection Screen -->
   <div id="portal-selection" class="min-h-full flex items-center justify-center p-4 fade-in">
    <div class="card-gradient rounded-3xl shadow-2xl p-8 md:p-12 max-w-lg w-full text-center">
     <div class="school-logo mx-auto mb-6">
      <svg class="w-12 h-12 text-white" fill="currentColor" viewbox="0 0 24 24"><path d="M12 3L1 9l4 2.18v6L12 21l7-3.82v-6l2-1.09V17h2V9L12 3zm6.82 6L12 12.72 5.18 9 12 5.28 18.82 9zM17 15.99l-5 2.73-5-2.73v-3.72L12 15l5-2.73v3.72z" />
      </svg>
     </div>
     <h1 id="school-title" class="text-3xl md:text-4xl font-bold text-gray-800 mb-2">MSIMBA DAY</h1>
     <p class="text-lg text-gray-600 mb-2">Secondary School</p>
     <p class="text-sm text-amber-600 font-medium mb-8">School Management System</p>
     <div class="space-y-4"><button onclick="showSchoolLogin()" class="btn-secondary w-full py-4 px-6 rounded-2xl text-white font-semibold text-lg flex items-center justify-center gap-3">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
       </svg> School Portal </button> <button onclick="showParentLogin()" class="btn-primary w-full py-4 px-6 rounded-2xl text-white font-semibold text-lg flex items-center justify-center gap-3">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
       </svg> Parent Portal </button>
     </div>
     <p class="mt-8 text-xs text-gray-500">© 2024 MSIMBA DAY Secondary School. All rights reserved.</p>
    </div>
   </div><!-- School Login Screen -->
   <div id="school-login" class="min-h-full flex items-center justify-center p-4 hidden">
    <div class="card-gradient rounded-3xl shadow-2xl p-8 md:p-10 max-w-md w-full fade-in"><button onclick="showPortalSelection()" class="text-gray-500 hover:text-gray-700 mb-4 flex items-center gap-2">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> Back </button>
     <div class="text-center mb-8">
      <div class="w-16 h-16 bg-gradient-to-br from-blue-900 to-blue-700 rounded-2xl flex items-center justify-center mx-auto mb-4">
       <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
       </svg>
      </div>
      <h2 class="text-2xl font-bold text-gray-800">School Portal Login</h2>
      <p class="text-gray-500 mt-1">Administrator Access Only</p>
     </div>
     <form id="school-login-form" onsubmit="handleSchoolLogin(event)" class="space-y-5">
      <div><label class="block text-sm font-medium text-gray-700 mb-2">Email Address</label> <input type="email" id="school-email" required class="input-styled w-full px-4 py-3 rounded-xl outline-none" placeholder="Enter school email">
      </div>
      <div><label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
       <div class="relative"><input type="password" id="school-password" required class="input-styled w-full px-4 py-3 rounded-xl outline-none pr-12" placeholder="Enter password"> <button type="button" onclick="togglePassword('school-password')" class="absolute right-4 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600">
         <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
         </svg></button>
       </div>
      </div>
      <div id="school-login-error" class="hidden text-red-500 text-sm bg-red-50 p-3 rounded-xl"></div><button type="submit" class="btn-secondary w-full py-4 rounded-xl text-white font-semibold text-lg"> Login to School Portal </button>
     </form>
    </div>
   </div><!-- Parent Login Screen -->
   <div id="parent-login" class="min-h-full flex items-center justify-center p-4 hidden">
    <div class="card-gradient rounded-3xl shadow-2xl p-8 md:p-10 max-w-md w-full fade-in"><button onclick="showPortalSelection()" class="text-gray-500 hover:text-gray-700 mb-4 flex items-center gap-2">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg> Back </button>
     <div class="text-center mb-8">
      <div class="w-16 h-16 bg-gradient-to-br from-amber-500 to-amber-600 rounded-2xl flex items-center justify-center mx-auto mb-4">
       <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
       </svg>
      </div>
      <h2 class="text-2xl font-bold text-gray-800">Parent Portal Login</h2>
      <p class="text-gray-500 mt-1">Access your child's information</p>
     </div>
     <form id="parent-login-form" onsubmit="handleParentLogin(event)" class="space-y-5">
      <div><label class="block text-sm font-medium text-gray-700 mb-2">Student Prime Number</label> <input type="text" id="parent-prime" required class="input-styled w-full px-4 py-3 rounded-xl outline-none" placeholder="Enter student's prime number">
      </div>
      <div><label class="block text-sm font-medium text-gray-700 mb-2">Parent Phone Number</label> <input type="tel" id="parent-phone" required class="input-styled w-full px-4 py-3 rounded-xl outline-none" placeholder="Enter your phone number">
      </div>
      <div id="parent-login-error" class="hidden text-red-500 text-sm bg-red-50 p-3 rounded-xl"></div><button type="submit" class="btn-primary w-full py-4 rounded-xl text-white font-semibold text-lg"> Login to Parent Portal </button>
     </form>
    </div>
   </div><!-- School Dashboard -->
   <div id="school-dashboard" class="min-h-full hidden"><!-- School Header -->
    <header class="bg-white shadow-lg sticky top-0 z-50">
     <div class="max-w-7xl mx-auto px-4 py-3 flex items-center justify-between">
      <div class="flex items-center gap-3">
       <div class="w-10 h-10 bg-gradient-to-br from-amber-500 to-amber-600 rounded-xl flex items-center justify-center">
        <svg class="w-6 h-6 text-white" fill="currentColor" viewbox="0 0 24 24"><path d="M12 3L1 9l4 2.18v6L12 21l7-3.82v-6l2-1.09V17h2V9L12 3z" />
        </svg>
       </div>
       <div>
        <h1 class="font-bold text-gray-800">MSIMBA DAY</h1>
        <p class="text-xs text-gray-500">School Administration</p>
       </div>
      </div>
      <div class="flex items-center gap-4"><button onclick="showSchoolNotifications()" class="relative p-2 hover:bg-gray-100 rounded-xl transition-colors">
        <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
        </svg><span id="school-notif-badge" class="absolute -top-1 -right-1 w-5 h-5 bg-red-500 text-white text-xs rounded-full flex items-center justify-center notification-badge hidden">0</span> </button> <button onclick="logoutSchool()" class="flex items-center gap-2 px-4 py-2 bg-gray-100 hover:bg-gray-200 rounded-xl transition-colors">
        <svg class="w-5 h-5 text-gray-600" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1" />
        </svg><span class="hidden md:inline">Logout</span> </button>
      </div>
     </div><!-- School Navigation -->
     <nav class="max-w-7xl mx-auto px-4 pb-3">
      <div class="flex gap-2 overflow-x-auto"><button onclick="showSchoolSection('students')" class="school-nav-btn px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap bg-blue-900 text-white" data-section="students"> 📚 Students </button> <button onclick="showSchoolSection('results')" class="school-nav-btn px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200" data-section="results"> 📊 Results </button> <button onclick="showSchoolSection('permissions')" class="school-nav-btn px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200" data-section="permissions"> 📋 Permissions </button> <button onclick="showSchoolSection('messages')" class="school-nav-btn px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200" data-section="messages"> 💬 Messages </button> <button onclick="showSchoolSection('announcements')" class="school-nav-btn px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200" data-section="announcements"> 📢 Announcements </button>
      </div>
     </nav>
    </header><!-- School Content -->
    <main class="max-w-7xl mx-auto p-4 pb-8"><!-- Students Section -->
     <section id="school-students" class="fade-in">
      <div class="card-gradient rounded-2xl p-6 mb-6">
       <h2 class="text-xl font-bold text-gray-800 mb-4 flex items-center gap-2"><span class="w-10 h-10 bg-blue-100 rounded-xl flex items-center justify-center">📝</span> Register New Student</h2>
       <form id="register-student-form" onsubmit="registerStudent(event)" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1">Student Name</label> <input type="text" id="student-name" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm" placeholder="Full name">
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1">Prime Number</label> <input type="text" id="student-prime" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm" placeholder="Unique ID">
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1">Parent Phone</label> <input type="tel" id="student-parent-phone" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm" placeholder="Phone number">
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1">Class/Form</label> <select id="student-form" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">Select Form</option> <option value="Form 1">Form 1</option> <option value="Form 2">Form 2</option> <option value="Form 3">Form 3</option> <option value="Form 4">Form 4</option> </select>
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1">Academic Year</label> <select id="student-year" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">Select Year</option> <option value="2024">2024</option> <option value="2025">2025</option> <option value="2026">2026</option> </select>
        </div>
        <div class="md:col-span-2 lg:col-span-3 flex items-end"><button type="submit" id="register-btn" class="btn-primary px-6 py-2 rounded-lg text-white font-medium"> Register Student </button>
        </div>
       </form>
      </div>
      <div class="card-gradient rounded-2xl p-6">
       <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-4">
        <h2 class="text-xl font-bold text-gray-800 flex items-center gap-2"><span class="w-10 h-10 bg-green-100 rounded-xl flex items-center justify-center">👨‍🎓</span> Registered Students</h2>
        <div class="flex gap-2"><select id="filter-form" onchange="filterStudents()" class="input-styled px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">All Forms</option> <option value="Form 1">Form 1</option> <option value="Form 2">Form 2</option> <option value="Form 3">Form 3</option> <option value="Form 4">Form 4</option> </select> <select id="filter-year" onchange="filterStudents()" class="input-styled px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">All Years</option> <option value="2024">2024</option> <option value="2025">2025</option> <option value="2026">2026</option> </select>
        </div>
       </div>
       <div class="overflow-x-auto">
        <table class="w-full">
         <thead>
          <tr class="table-header text-white text-left">
           <th class="px-4 py-3 rounded-tl-xl text-sm font-medium">Prime No.</th>
           <th class="px-4 py-3 text-sm font-medium">Student Name</th>
           <th class="px-4 py-3 text-sm font-medium">Form</th>
           <th class="px-4 py-3 text-sm font-medium">Year</th>
           <th class="px-4 py-3 text-sm font-medium">Parent Phone</th>
           <th class="px-4 py-3 rounded-tr-xl text-sm font-medium">Actions</th>
          </tr>
         </thead>
         <tbody id="students-table-body" class="divide-y divide-gray-100">
          <tr>
           <td colspan="6" class="px-4 py-8 text-center text-gray-500">No students registered yet</td>
          </tr>
         </tbody>
        </table>
       </div>
      </div>
     </section><!-- Results Section -->
     <section id="school-results" class="hidden fade-in">
      <div class="card-gradient rounded-2xl p-6 mb-6">
       <h2 class="text-xl font-bold text-gray-800 mb-4 flex items-center gap-2"><span class="w-10 h-10 bg-purple-100 rounded-xl flex items-center justify-center">📊</span> Upload Examination Results</h2>
       <form id="upload-results-form" onsubmit="uploadResults(event)">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-4">
         <div><label class="block text-sm font-medium text-gray-700 mb-1">Select Student</label> <select id="result-student" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">Choose student...</option> </select>
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1">Examination Type</label> <select id="exam-type" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">Select exam type...</option> <option value="Monthly Test">Monthly Test</option> <option value="Mid-Term Exam">Mid-Term Exam</option> <option value="Terminal Exam">Terminal Exam</option> <option value="Annual Exam">Annual Exam</option> <option value="Mock Exam">Mock Exam</option> <option value="National Exam">National Exam</option> </select>
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1">Academic Year</label> <select id="result-year" required class="input-styled w-full px-3 py-2 rounded-lg outline-none text-sm bg-white"> <option value="">Select year...</option> <option value="2024">2024</option> <option value="2025">2025</option> <option value="2026">2026</option> </select>
         </div>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-3 mb-4">
         <div><label class="block text-xs font-medium text-gray-600 mb-1">Civics</label> <input type="number" id="mark-civics" min
