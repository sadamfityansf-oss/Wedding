<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>دعوة زفاف - مصطفى & أماني</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Reem+Kufi:wght@400;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome & Canvas Confetti -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        :root {
            --bg-dark: #090204;
            --card-bg: rgba(22, 7, 12, 0.85);
            --gold-primary: #d4af37;
            --gold-light: #fdf0a6;
            --gold-glow: rgba(212, 175, 55, 0.4);
            --text-light: #f8f4f5;
            --text-muted: #c9b0b5;
            --border-gold: rgba(212, 175, 55, 0.5);
            --ruby-red: #58111e;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            user-select: none;
            -webkit-user-select: none;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-light);
            font-family: 'Amiri', serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px 15px;
            overflow-x: hidden;
            position: relative;
            background: radial-gradient(circle at center, #26070f 0%, #090204 100%);
        }

        /* جزيئات الخلفية المتحركة */
        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        /* بطاقة الدعوة الرئيسية */
        .invitation-card {
            background: var(--card-bg);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 2px solid var(--gold-primary);
            border-radius: 24px;
            padding: 45px 25px;
            max-width: 520px;
            width: 100%;
            text-align: center;
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.9), 0 0 30px rgba(212, 175, 55, 0.2);
            position: relative;
            z-index: 2;
            outline: 1px solid var(--border-gold);
            outline-offset: -10px;
            animation: cardGlow 4s infinite alternate ease-in-out, fadeInUp 1.2s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes cardGlow {
            0% { box-shadow: 0 20px 50px rgba(0, 0, 0, 0.9), 0 0 20px rgba(212, 175, 55, 0.2); }
            100% { box-shadow: 0 25px 60px rgba(0, 0, 0, 0.95), 0 0 40px rgba(212, 175, 55, 0.4); }
        }

        /* عناصر الزخرفة بالزوايا */
        .corner-ornament {
            position: absolute;
            width: 40px;
            height: 40px;
            border: 2px solid var(--gold-primary);
            pointer-events: none;
        }

        .corner-tl { top: 18px; left: 18px; border-right: none; border-bottom: none; }
        .corner-tr { top: 18px; right: 18px; border-left: none; border-bottom: none; }
        .corner-bl { bottom: 18px; left: 18px; border-right: none; border-top: none; }
        .corner-br { bottom: 18px; right: 18px; border-left: none; border-top: none; }

        /* العناصر بنظام الظهور المتتابع */
        .animate-item {
            opacity: 0;
            transform: translateY(20px);
            animation: slideUpFade 0.8s ease forwards;
        }

        .delay-1 { animation-delay: 0.2s; }
        .delay-2 { animation-delay: 0.4s; }
        .delay-3 { animation-delay: 0.6s; }
        .delay-4 { animation-delay: 0.8s; }
        .delay-5 { animation-delay: 1.0s; }
        .delay-6 { animation-delay: 1.2s; }

        @keyframes slideUpFade {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .bismillah {
            font-size: 1.35rem;
            color: var(--gold-light);
            margin-bottom: 20px;
            letter-spacing: 1px;
            text-shadow: 0 2px 8px rgba(0,0,0,0.5);
        }

        .header-title {
            font-family: 'Reem Kufi', sans-serif;
            font-size: 2.2rem;
            color: var(--gold-primary);
            margin-bottom: 15px;
            letter-spacing: 1px;
            background: linear-gradient(135deg, #ffe89e 0%, #d4af37 50%, #9e7a18 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .family-text {
            font-size: 1.1rem;
            color: var(--text-muted);
            line-height: 1.9;
            margin-bottom: 20px;
        }

        .names-wrapper {
            margin: 25px 0;
            position: relative;
        }

        .couple-names {
            font-family: 'Reem Kufi', sans-serif;
            font-size: 2.9rem;
            color: var(--gold-light);
            line-height: 1.2;
            text-shadow: 0 0 20px rgba(212, 175, 55, 0.4);
            display: inline-block;
            transition: transform 0.3s ease;
        }

        .couple-names:hover {
            transform: scale(1.05);
        }

        .ampersand {
            font-size: 2rem;
            color: var(--gold-primary);
            margin: 8px 0;
            display: block;
            animation: pulseGlow 2s infinite alternate;
        }

        @keyframes pulseGlow {
            from { transform: scale(1); opacity: 0.8; }
            to { transform: scale(1.2); opacity: 1; text-shadow: 0 0 15px var(--gold-primary); }
        }

        .details-box {
            border-top: 1px dashed var(--border-gold);
            border-bottom: 1px dashed var(--border-gold);
            padding: 22px 10px;
            margin: 25px 0;
            line-height: 2.1;
            font-size: 1.15rem;
            background: rgba(212, 175, 55, 0.03);
            border-radius: 12px;
        }

        .highlight {
            color: var(--gold-light);
            font-weight: bold;
        }

        /* العداد التنازلي */
        .timer-title {
            font-size: 0.95rem;
            color: var(--gold-primary);
            margin-bottom: 10px;
            font-family: 'Reem Kufi', sans-serif;
        }

        .timer-container {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin: 15px 0 30px;
        }

        .timer-box {
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid var(--border-gold);
            border-radius: 12px;
            padding: 12px 8px;
            min-width: 72px;
            transition: all 0.3s ease;
            box-shadow: inset 0 0 10px rgba(212, 175, 55, 0.05);
        }

        .timer-box:hover {
            transform: translateY(-5px);
            border-color: var(--gold-primary);
            box-shadow: 0 5px 15px rgba(212, 175, 55, 0.2);
        }

        .timer-number {
            font-size: 1.6rem;
            color: var(--gold-light);
            font-weight: bold;
            font-family: 'Reem Kufi', sans-serif;
            line-height: 1;
        }

        .timer-label {
            font-size: 0.75rem;
            color: var(--text-muted);
            margin-top: 5px;
        }

        /* الأزرار التفاعلية */
        .btn-group {
            display: flex;
            flex-direction: column;
            gap: 14px;
            margin-top: 20px;
        }

        .btn {
            background: linear-gradient(135deg, rgba(212, 175, 55, 0.1) 0%, rgba(88, 17, 30, 0.3) 100%);
            color: var(--gold-light);
            border: 1px solid var(--gold-primary);
            padding: 14px 22px;
            border-radius: 35px;
            text-decoration: none;
            font-size: 1.05rem;
            font-weight: bold;
            font-family: 'Reem Kufi', sans-serif;
            transition: all 0.35s ease;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
        }

        .btn:hover {
            background: var(--gold-primary);
            color: #000;
            box-shadow: 0 0 25px rgba(212, 175, 55, 0.5);
            transform: translateY(-2px);
        }

        .btn-rsvp {
            background: linear-gradient(135deg, var(--gold-primary) 0%, #aa8212 100%);
            color: #000;
        }

        .btn-rsvp:hover {
            background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold-primary) 100%);
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.7);
        }

        /* مشغل الموسيقى العائم */
        .audio-control-floating {
            position: fixed;
            top: 25px;
            left: 25px;
            z-index: 10;
            background: rgba(22, 7, 12, 0.85);
            border: 1px solid var(--gold-primary);
            border-radius: 50px;
            padding: 8px 16px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(0,0,0,0.5);
            backdrop-filter: blur(5px);
            transition: all 0.3s ease;
        }

        .audio-control-floating:hover {
            transform: scale(1.05);
            border-color: var(--gold-light);
        }

        .sound-wave {
            display: flex;
            align-items: flex-end;
            gap: 3px;
            height: 16px;
        }

        .sound-wave span {
            width: 3px;
            height: 100%;
            background-color: var(--gold-primary);
            border-radius: 3px;
            animation: soundWave 1.2s infinite ease-in-out;
            animation-play-state: paused;
        }

        .sound-wave.playing span {
            animation-play-state: running;
        }

        .sound-wave span:nth-child(1) { animation-delay: 0.1s; }
        .sound-wave span:nth-child(2) { animation-delay: 0.3s; }
        .sound-wave span:nth-child(3) { animation-delay: 0.2s; }
        .sound-wave span:nth-child(4) { animation-delay: 0.4s; }

        @keyframes soundWave {
            0%, 100% { height: 4px; }
            50% { height: 16px; }
        }

        /* النافذة المنبثقة للتأكيد RSVP */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(8px);
            z-index: 100;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            pointer-events: none;
            transition: all 0.4s ease;
            padding: 20px;
        }

        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal-card {
            background: var(--card-bg);
            border: 2px solid var(--gold-primary);
            border-radius: 20px;
            padding: 30px 25px;
            max-width: 420px;
            width: 100%;
            text-align: center;
            position: relative;
            transform: scale(0.8);
            transition: all 0.4s ease;
            box-shadow: 0 20px 50px rgba(0,0,0,0.9);
        }

        .modal-overlay.active .modal-card {
            transform: scale(1);
        }

        .modal-close {
            position: absolute;
            top: 15px;
            left: 15px;
            color: var(--gold-primary);
            font-size: 1.2rem;
            cursor: pointer;
            background: none;
            border: none;
        }

        .modal-title {
            font-family: 'Reem Kufi', sans-serif;
            color: var(--gold-light);
            font-size: 1.6rem;
            margin-bottom: 15px;
        }

        .form-input {
            width: 100%;
            padding: 12px 15px;
            margin-bottom: 15px;
            background: rgba(0,0,0,0.5);
            border: 1px solid var(--border-gold);
            border-radius: 10px;
            color: #fff;
            font-family: 'Amiri', serif;
            font-size: 1rem;
            outline: none;
        }

        .form-input:focus {
            border-color: var(--gold-primary);
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.3);
        }

        .footer-note {
            margin-top: 25px;
            font-size: 0.95rem;
            color: var(--text-muted);
            font-style: italic;
        }

        /* شاشة البدء للتشغيل الصوتي تلقائياً */
        .welcome-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #090204;
            z-index: 200;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: opacity 0.8s ease, visibility 0.8s ease;
            padding: 20px;
            text-align: center;
        }

        .welcome-overlay.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .welcome-btn {
            background: linear-gradient(135deg, var(--gold-primary) 0%, #aa8212 100%);
            color: #000;
            border: none;
            padding: 16px 36px;
            font-size: 1.3rem;
            font-family: 'Reem Kufi', sans-serif;
            border-radius: 40px;
            cursor: pointer;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.6);
            animation: pulseBtn 1.8s infinite;
            margin-top: 25px;
        }

        @keyframes pulseBtn {
            0% { transform: scale(1); box-shadow: 0 0 20px rgba(212, 175, 55, 0.5); }
            50% { transform: scale(1.06); box-shadow: 0 0 35px rgba(212, 175, 55, 0.8); }
            100% { transform: scale(1); box-shadow: 0 0 20px rgba(212, 175, 55, 0.5); }
        }

        @media (max-width: 480px) {
            .invitation-card { padding: 35px 18px; }
            .header-title { font-size: 1.8rem; }
            .couple-names { font-size: 2.3rem; }
            .details-box { font-size: 1.05rem; }
            .timer-box { min-width: 62px; padding: 10px 4px; }
            .timer-number { font-size: 1.3rem; }
            .audio-control-floating { top: 15px; left: 15px; padding: 6px 12px; font-size: 0.85rem; }
        }
    </style>
</head>
<body>

    <!-- جزيئات الخلفية المتلألئة -->
    <canvas id="particles-canvas"></canvas>

    <!-- شاشة الترحيب لتشغيل الموسيقى -->
    <div class="welcome-overlay" id="welcomeOverlay">
        <h2 style="color: var(--gold-light); font-family: 'Reem Kufi', sans-serif; font-size: 2.2rem; margin-bottom: 10px;">دعوة زفاف</h2>
        <p style="color: var(--text-muted); font-size: 1.2rem;">مصطفى & أماني</p>
        <button class="welcome-btn" onclick="startInvitation()">
            <i class="fa-solid fa-envelope-open-text"></i> فتح الدعوة
        </button>
    </div>

    <!-- زر التحكم بالصوت العائم -->
    <div class="audio-control-floating" onclick="toggleAudio()">
        <i id="audioIcon" class="fa-solid fa-music" style="color: var(--gold-primary);"></i>
        <div class="sound-wave" id="soundWave">
            <span></span><span></span><span></span><span></span>
        </div>
    </div>

    <!-- بطاقة الدعوة الرئيسية -->
    <div class="invitation-card">
        <!-- زوايا الزخرفة -->
        <div class="corner-ornament corner-tl"></div>
        <div class="corner-ornament corner-tr"></div>
        <div class="corner-ornament corner-bl"></div>
        <div class="corner-ornament corner-br"></div>

        <div class="bismillah animate-item delay-1">بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ</div>
        
        <h1 class="header-title animate-item delay-2">دعوة زفاف مباركة</h1>
        
        <p class="family-text animate-item delay-3">
            تتشرف <b>آل مصطفى (العريس)</b><br>
            و <b>آل فتيان (العروس)</b><br>
            بدعوتكم لحضور حفل زفاف أبنائهم
        </p>

        <div class="names-wrapper animate-item delay-4">
            <div class="couple-names">مصطفى</div>
            <span class="ampersand">&</span>
            <div class="couple-names">أماني</div>
        </div>

        <div class="details-box animate-item delay-5">
            <p><i class="fa-regular fa-calendar-days" style="color:var(--gold-primary);"></i> <b>اليوم والتاريخ:</b> الاثنين <span class="highlight">19-10-2026</span></p>
            <p><i class="fa-regular fa-clock" style="color:var(--gold-primary);"></i> <b>الوقت:</b> من <span class="highlight">8:30 مساءً</span> إلى <span class="highlight">11:00 مساءً</span></p>
            <p><i class="fa-solid fa-location-dot" style="color:var(--gold-primary);"></i> <b>المكان:</b> فندق سراج - جبل الحسين</p>
            <p style="font-size: 0.9rem; color: var(--text-muted); margin-top: 2px;">(بجانب مستشفى الكندي)</p>
        </div>

        <!-- العداد التنازلي -->
        <div class="animate-item delay-6">
            <div class="timer-title">💡 المتبقي على الليلة الموعودة</div>
            <div class="timer-container">
                <div class="timer-box">
                    <div id="days" class="timer-number">00</div>
                    <div class="timer-label">يوم</div>
                </div>
                <div class="timer-box">
                    <div id="hours" class="timer-number">00</div>
                    <div class="timer-label">ساعة</div>
                </div>
                <div class="timer-box">
                    <div id="minutes" class="timer-number">00</div>
                    <div class="timer-label">دقيقة</div>
                </div>
                <div class="timer-box">
                    <div id="seconds" class="timer-number">00</div>
                    <div class="timer-label">ثانية</div>
                </div>
            </div>
        </div>

        <!-- مجموعة الأزرار التفاعلية -->
        <div class="btn-group animate-item delay-6">
            <button onclick="openRsvpModal()" class="btn btn-rsvp">
                <i class="fa-solid fa-heart"></i> تأكيد الحضور (RSVP)
            </button>
            <a href="https://maps.google.com/?q=Siraj+Hotel+Amman" target="_blank" class="btn">
                <i class="fa-solid fa-map-location-dot"></i> موقع الفندق على الخريطة
            </a>
            <button onclick="addToCalendar()" class="btn">
                <i class="fa-regular fa-calendar-plus"></i> إضافة إلى تقويم Google
            </button>
        </div>

        <p class="footer-note animate-item delay-6">حضوركم يكتمل به فرحنا ويسعد أرواحنا ✨</p>
    </div>

    <!-- نافذة تأكيد الحضور (RSVP Modal) -->
    <div class="modal-overlay" id="rsvpModal">
        <div class="modal-card">
            <button class="modal-close" onclick="closeRsvpModal()"><i class="fa-solid fa-xmark"></i></button>
            <h3 class="modal-title">تأكيد الحضور</h3>
            <p style="color: var(--text-muted); margin-bottom: 20px; font-size: 0.95rem;">يسعدنا جداً حضوركم ومشاركتنا فرحتنا!</p>
            <form id="rsvpForm" onsubmit="submitRsvp(event)">
                <input type="text" class="form-input" placeholder="الاسم الكريم" required>
                <input type="number" class="form-input" placeholder="عدد المرافقين" min="1" max="10" value="1" required>
                <button type="submit" class="btn btn-rsvp" style="width: 100%; border: none;">
                    <i class="fa-solid fa-paper-plane"></i> إرسال التأكيد
                </button>
            </form>
        </div>
    </div>

    <script>
        // ----------------------------------------------------
        // 1. نظام البرمجة الصوتية الرومانسية (Web Audio API Synthesizer)
        // ----------------------------------------------------
        let audioCtx = null;
        let isPlaying = false;
        let audioInterval = null;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
        }

        // عزف نغمة رومانسية ناعمة وشعبيّة هادئة
        function playRomanticNote() {
            if (!audioCtx || !isPlaying) return;

            const notes = [261.63, 293.66, 329.63, 349.23, 392.00, 440.00, 493.88, 523.25]; // سلم Do الكبير
            const melody = [329.63, 392.00, 440.00, 523.25, 493.88, 440.00, 392.00, 329.63];
            const randomNote = melody[Math.floor(Math.random() * melody.length)];

            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();

            osc.type = 'sine';
            osc.frequency.setValueAtTime(randomNote, audioCtx.currentTime);

            gain.gain.setValueAtTime(0.01, audioCtx.currentTime);
            gain.gain.exponentialRampToValueAtTime(0.12, audioCtx.currentTime + 0.4);
            gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 2.5);

            osc.connect(gain);
            gain.connect(audioCtx.destination);

            osc.start();
            osc.stop(audioCtx.currentTime + 2.6);
        }

        function toggleAudio() {
            initAudio();
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }

            isPlaying = !isPlaying;
            const soundWave = document.getElementById('soundWave');
            const audioIcon = document.getElementById('audioIcon');

            if (isPlaying) {
                soundWave.classList.add('playing');
                audioIcon.className = "fa-solid fa-volume-high";
                playRomanticNote();
                audioInterval = setInterval(playRomanticNote, 1400);
            } else {
                soundWave.classList.remove('playing');
                audioIcon.className = "fa-solid fa-volume-xmark";
                clearInterval(audioInterval);
            }
        }

        function startInvitation() {
            document.getElementById('welcomeOverlay').classList.add('hidden');
            toggleAudio(); // بدء تشغيل النغمات فور فتح البطاقة
        }

        // ----------------------------------------------------
        // 2. العداد التنازلي لحفل الزفاف
        // ----------------------------------------------------
        const targetDate = new Date("October 19, 2026 19:30:00").getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const difference = targetDate - now;

            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((difference % (1000 * 60)) / 1000);

                document.getElementById("days").innerText = days.toString().padStart(2, '0');
                document.getElementById("hours").innerText = hours.toString().padStart(2, '0');
                document.getElementById("minutes").innerText = minutes.toString().padStart(2, '0');
                document.getElementById("seconds").innerText = seconds.toString().padStart(2, '0');
            } else {
                document.querySelector(".timer-container").innerHTML = "<p style='color:var(--gold-primary); font-weight:bold; font-size:1.2rem;'>أهلاً وسهلاً بكم في حفل زفافنا الليلة!</p>";
            }
        }

        setInterval(updateCountdown, 1000);
        updateCountdown();

        // ----------------------------------------------------
        // 3. إضافة الموعد إلى التقويم
        // ----------------------------------------------------
        function addToCalendar() {
            const title = encodeURIComponent("حفل زفاف مصطفى & أماني");
            const details = encodeURIComponent("حفل زفاف مصطفى (عائلة مصطفى) وأماني (عائلة فتيان) في فندق سراج - جبل الحسين.");
            const location = encodeURIComponent("فندق سراج، جبل الحسين، عمان");
            const calendarUrl = `https://calendar.google.com/calendar/render?action=TEMPLATE&text=${title}&dates=20261019T163000Z/20261019T200000Z&details=${details}&location=${location}`;
            window.open(calendarUrl, '_blank');
        }

        // ----------------------------------------------------
        // 4. النافذة المنبثقة للتأكيد RSVP مع تأثير القصاصات الذهبية
        // ----------------------------------------------------
        function openRsvpModal() {
            document.getElementById('rsvpModal').classList.add('active');
        }

        function closeRsvpModal() {
            document.getElementById('rsvpModal').classList.remove('active');
        }

        function submitRsvp(event) {
            event.preventDefault();
            closeRsvpModal();

            // إطلاق قصاصات الاحتفال الفاخرة (Gold Confetti)
            if (typeof confetti === 'function') {
                confetti({
                    particleCount: 120,
                    spread: 80,
                    origin: { y: 0.6 },
                    colors: ['#d4af37', '#fdf0a6', '#ffffff', '#58111e']
                });
            }

            alert("شكراً لتأكيد حضوركم! ننتظركم بشوق ومحبة ❤️");
        }

        // ----------------------------------------------------
        // 5. محاكاة الجزيئات البصرية الذهبية والمتلألئة (Bokeh / Sparkles)
        // ----------------------------------------------------
        const canvas = document.getElementById('particles-canvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() {
                this.reset();
            }

            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height + canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedY = Math.random() * 1 + 0.3;
                this.speedX = (Math.random() - 0.5) * 0.5;
                this.opacity = Math.random() * 0.7 + 0.2;
                this.color = Math.random() > 0.3 ? '#d4af37' : '#fdf0a6';
            }

            update() {
                this.y -= this.speedY;
                this.x += this.speedX;
                if (this.y < -10) {
                    this.reset();
                    this.y = canvas.height + 10;
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.globalAlpha = this.opacity;
                ctx.shadowBlur = 10;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.globalAlpha = 1.0;
            }
        }

        const particlesArray = Array.from({ length: 45 }, () => new Particle());

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particlesArray.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animateParticles);
        }

        animateParticles();
    </script>
</body>
</html>
