<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>دعوة زفاف - أحمد & فاطمة</title>
    <!-- استيراد خطوط عربية فاخرة وأيقونات -->
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary-dark: #3a0d14; /* مصظفى تيسير مصطفى */
            --accent-gold: #c5a059;   /* ذهبي دافئ */
            --light-bg: #fcf9f5;      /* خلفية كريمية ناعمة */
            --text-color: #2b2b2b;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background-color: var(--primary-dark);
            color: var(--text-color);
            overflow-x: hidden;
            direction: rtl;
        }

        h1, h2, h3, .names-font {
            font-family: 'Amiri', serif;
        }

        /* نافذة الظرف الافتتاحية */
        #envelope-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #2b080c, #4a121b);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.8s ease, visibility 0.8s ease;
        }

        .envelope-card {
            background: var(--light-bg);
            width: 90%;
            max-width: 450px;
            padding: 40px 20px;
            text-align: center;
            border-radius: 12px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
            border: 2px solid var(--accent-gold);
            position: relative;
        }

        .wax-seal {
            width: 80px;
            height: 80px;
            background-color: var(--primary-dark);
            border: 3px solid var(--accent-gold);
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--accent-gold);
            font-size: 32px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .open-btn {
            background: var(--primary-dark);
            color: var(--accent-gold);
            border: 2px solid var(--accent-gold);
            padding: 12px 35px;
            font-size: 18px;
            font-family: 'Cairo', sans-serif;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
            font-weight: 600;
        }

        .open-btn:hover {
            background: var(--accent-gold);
            color: var(--primary-dark);
        }

        /* المحتوى الرئيسي للموقع */
        #main-content {
            display: none;
            opacity: 0;
            transition: opacity 1s ease;
            background-color: var(--light-bg);
            min-height: 100vh;
        }

        .show-content {
            display: block !important;
            opacity: 1 !important;
        }

        /* الهيدر وغلاف الدعوة */
        header {
            text-align: center;
            padding: 60px 20px;
            background: linear-gradient(to bottom, #4a121b, #3a0d14);
            color: #fff;
            border-bottom: 4px solid var(--accent-gold);
        }

        header h3 {
            color: var(--accent-gold);
            letter-spacing: 3px;
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        header h1 {
            font-size: 3rem;
            color: #fff;
            margin-bottom: 15px;
        }

        header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* الأقسام العامة */
        section {
            padding: 60px 20px;
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .section-title {
            color: var(--primary-dark);
            font-size: 2.2rem;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 2px;
            background-color: var(--accent-gold);
        }

        /* بطاقة العروسين */
        .couple-container {
            display: flex;
            flex-direction: column;
            gap: 30px;
            align-items: center;
            margin-top: 30px;
        }

        .person-card {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            width: 100%;
            max-width: 400px;
            border-right: 4px solid var(--accent-gold);
        }

        .person-card h3 {
            color: var(--primary-dark);
            font-size: 1.8rem;
        }

        /* عداد التنازلي */
        .countdown-box {
            background: #fff5f5;
            border: 1px solid #ebd3d3;
            border-radius: 12px;
            padding: 30px;
            margin: 40px auto;
            max-width: 600px;
        }

        .countdown-timers {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
        }

        .time-block span {
            display: block;
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary-dark);
        }

        .time-block label {
            font-size: 0.9rem;
            color: #666;
        }

        /* الجدول الزمني / الفعاليات */
        .timeline {
            position: relative;
            margin-top: 30px;
            text-align: right;
            border-right: 2px solid var(--accent-gold);
            padding-right: 20px;
        }

        .timeline-item {
            margin-bottom: 30px;
            position: relative;
        }

        .timeline-item i {
            position: absolute;
            right: -31px;
            top: 0;
            background: var(--accent-gold);
            color: #fff;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            text-align: center;
            font-size: 12px;
            line-height: 20px;
        }

        .timeline-item h4 {
            color: var(--primary-dark);
            font-size: 1.3rem;
        }

        /* زر الخريطة والهدايا */
        .btn-action {
            display: inline-block;
            background: var(--primary-dark);
            color: var(--accent-gold);
            padding: 12px 30px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: bold;
            margin-top: 15px;
            border: 1px solid var(--accent-gold);
            transition: 0.3s;
        }

        .btn-action:hover {
            background: var(--accent-gold);
            color: var(--primary-dark);
        }

        /* مشغل الموسيقى العائم */
        #music-control {
            position: fixed;
            bottom: 20px;
            left: 20px;
            background: var(--primary-dark);
            color: var(--accent-gold);
            border: 2px solid var(--accent-gold);
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 1000;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            font-size: 20px;
        }

        footer {
            background: var(--primary-dark);
            color: var(--accent-gold);
            text-align: center;
            padding: 30px;
            font-size: 1rem;
            border-top: 2px solid var(--accent-gold);
        }
    </style>
</head>
<body>

    <!-- واجهة الظرف الافتتاحية -->
    <div id="envelope-overlay">
        <div class="envelope-card">
            <div class="wax-seal">
                <i class="fa-solid fa-heart"></i>
            </div>
            <h3 style="color: var(--primary-dark); font-size: 1.5rem; margin-bottom: 10px;">دعوة زفاف مباركة</h3>
            <p style="color: #666; margin-bottom: 20px; font-size: 0.95rem;">يسرنا دعوتكم لحضور حفل زفافنا بشغف وفرح</p>
            <h2 class="names-font" style="color: var(--primary-dark); font-size: 2rem; margin-bottom: 20px;">أحمد & فاطمة</h2>
            <button class="open-btn" onclick="openInvitation()">اضغط لفتح الدعوة</button>
        </div>
    </div>

    <!-- مشغل الموسيقى الخلفية -->
    <audio id="bgMusic" loop>
        <!-- يمكنك استبدال الرابط بأي ملف MP3 تود تشغيله -->
        <source src="https://www.bensound.com/bensound-music/bensound-tenderness.mp3" type="audio/mpeg">
    </audio>

    <div id="music-control" onclick="toggleMusic()" title="تشغيل/إيقاف الموسيقى">
        <i id="music-icon" class="fa-solid fa-music"></i>
    </div>

    <!-- المحتوى الرئيسي للدعوة -->
    <div id="main-content">
        <header>
            <h3>حفل زفاف سعيد</h3>
            <h1 class="names-font">مصطفى & أماني</h1>
            <p><i class="fa-regular fa-calendar-days"></i> الجمعة، 25 ديسمبر 2026</p>
        </header>

        <section>
            <h2 class="section-title">أهلاً بكم في ليلتنا العمرية</h2>
            <p style="line-height: 1.8; color: #555; margin-top: 20px;">
                "وَمِنْ آيَاتِهِ أَنْ خَلَقَ لَكُم مِّنْ أَنفُسِكُمْ أَزْوَاجًا لِّتَسْكُنُوا إِلَيْهَا وَجَعَلَ بَيْنَكُم مَّوَدَّةً وَرَحْمَةً"
                <br>نتشرف بحضوركم وتشاركونا أجمل لحظات العمر.
            </p>

            <div class="couple-container">
                <div class="person-card">
                    <h3 class="names-font">مصطفى تيسير</h3>
                    <p style="color: #666; font-size: 0.9rem; margin-top: 5px;">العريس</p>
                </div>
                <div style="color: var(--accent-gold); font-size: 24px;"><i class="fa-solid fa-ring"></i></div>
                <div class="person-card">
                    <h3 class="names-font">أماني فتياند</h3>
                    <p style="color: #666; font-size: 0.9rem; margin-top: 5px;">العروس</p>
                </div>
            </div>
        </section>

        <!-- عداد تنازلي -->
        <section style="background-color: #fff; padding: 40px 20px;">
            <div class="countdown-box">
                <h2 class="section-title" style="font-size: 1.8rem;">ننتظر لقاءكم بشغف بعد</h2>
                <div class="countdown-timers">
                    <div class="time-block">
                        <span id="days">00</span>
                        <label>يوم</label>
                    </div>
                    <div class="time-block">
                        <span id="hours">00</span>
                        <label>ساعة</label>
                    </div>
                    <div class="time-block">
                        <span id="minutes">00</span>
                        <label>دقيقة</label>
                    </div>
                    <div class="time-block">
                        <span id="seconds">00</span>
                        <label>ثانية</label>
                    </div>
                </div>
            </div>
        </section>

        <!-- تفاصيل الحفل والمكان -->
        <section>
            <h2 class="section-title">برنامج الحفل والمكان</h2>
            <div class="timeline" style="max-width: 500px; margin: 30px auto 0;">
                <div class="timeline-item">
                    <i class="fa-solid fa-check"></i>
                    <h4>استقبال الضيوف</h4>
                    <p style="color: #666;">الساعة 07:00 مساءً</p>
                </div>
                <div class="timeline-item">
                    <i class="fa-solid fa-check"></i>
                    <h4>مراسم عقد القران والزفاف</h4>
                    <p style="color: #666;">الساعة 08:30 مساءً</p>
                </div>
                <div class="timeline-item">
                    <i class="fa-solid fa-check"></i>
                    <h4>مأبة العشاء</h4>
                    <p style="color: #666;">الساعة 10:00 مساءً</p>
                </div>
            </div>

            <div style="margin-top: 40px;">
                <p style="margin-bottom: 10px; font-weight: bold;"><i class="fa-solid fa-location-dot" style="color: var(--primary-dark);"></i> قاعة الملكي للاحتفالات - شارع الرئاسة</p>
                <a href="https://maps.google.com" target="_blank" class="btn-action">فتح الموقع على خريطة جوجل</a>
            </div>
        </section>

        <footer>
            <p class="names-font" style="font-size: 1.5rem; margin-bottom: 5px;">أحمد & فاطمة</p>
            <p style="font-size: 0.85rem; opacity: 0.8;">نتشرف بوجودكم لتمام فرحتنا</p>
        </footer>
    </div>

    <script>
        // تشغيل واجهة الدعوة وإطلاق الموسيقى الخلفية عند النقر على فتح الظرف
        function openInvitation() {
            const overlay = document.getElementById('envelope-overlay');
            const mainContent = document.getElementById('main-content');
            const music = document.getElementById('bgMusic');

            overlay.style.opacity = '0';
            setTimeout(() => {
                overlay.style.visibility = 'hidden';
                mainContent.classList.add('show-content');
            }, 800);

            // تشغيل الموسيقى
            music.play().catch(error => {
                console.log("Audio autoplay prevented by browser", error);
            });
        }

        // التحكم اليدوي بالموسيقى (تشغيل/إيقاف)
        function toggleMusic() {
            const music = document.getElementById('bgMusic');
            const icon = document.getElementById('music-icon');
            
            if (music.paused) {
                music.play();
                icon.className = "fa-solid fa-music";
            } else {
                music.pause();
                icon.className = "fa-solid fa-volume-xmark";
            }
        }

        // ضبط تاريخ العد التنازلي (يمكنك تعديل التاريخ والوقت أدناه)
        const weddingDate = new Date("Dec 25, 2026 19:00:00").getTime();

        const timer = setInterval(function() {
            const now = new Date().getTime();
            const distance = weddingDate - now;

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById("days").innerText = days < 10 ? "0" + days : days;
            document.getElementById("hours").innerText = hours < 10 ? "0" + hours : hours;
            document.getElementById("minutes").innerText = minutes < 10 ? "0" + minutes : minutes;
            document.getElementById("seconds").innerText = seconds < 10 ? "0" + seconds : seconds;

            if (distance < 0) {
                clearInterval(timer);
                document.querySelector(".countdown-box").innerHTML = "<h3 style='color:var(--primary-dark)'>لقد حان موعد حفلنا السعيد!</h3>";
            }
        }, 1000);
    </script>
</body>
</html>
