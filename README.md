<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تقديم الجامعات السودانية - توقعات الانسحاب</title>
    <style>
        :root {
            --primary: #005a36; /* أخضر مستوحى من الهوية الأكاديمية */
            --primary-dark: #003d24;
            --accent: #d4af37;  /* ذهبي */
            --bg: #f4f7f6;
            --card-bg: #ffffff;
            --text-main: #2d3748;
            --text-muted: #718096;
            --danger: #e53e3e;
            --warning: #dd6b20;
            --success: #38a169;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text-main);
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 850px;
            margin: 0 auto;
        }

        /* رأس الصفحة - العنوان العريض */
        header {
            text-align: center;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            padding: 35px 20px;
            border-radius: 16px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            margin-bottom: 25px;
            border-bottom: 4px solid var(--accent);
        }

        header h1 {
            font-size: 2.8rem;
            font-weight: 900;
            margin-bottom: 8px;
            letter-spacing: -0.5px;
        }

        header p {
            font-size: 1.15rem;
            opacity: 0.9;
        }

        /* كروت الإحصاءات السريعة */
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .summary-card {
            background: var(--card-bg);
            padding: 18px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
            border-top: 4px solid var(--primary);
        }

        .summary-card h3 {
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-bottom: 6px;
        }

        .summary-card .number {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--primary);
        }

        /* قسم أداة المحاكاة */
        .simulator {
            background: var(--card-bg);
            padding: 22px;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
            margin-bottom: 30px;
        }

        .simulator h3 {
            margin-bottom: 15px;
            font-size: 1.2rem;
            color: var(--primary-dark);
        }

        .slider-box {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        input[type=range] {
            flex-grow: 1;
            height: 8px;
            border-radius: 5px;
            accent-color: var(--primary);
            cursor: pointer;
        }

        .slider-value {
            font-size: 1.3rem;
            font-weight: bold;
            min-width: 60px;
            text-align: center;
            background: #edf2f7;
            padding: 4px 10px;
            border-radius: 8px;
        }

        .calc-result {
            margin-top: 15px;
            display: flex;
            justify-content: space-between;
            background: #f7fafc;
            padding: 12px 18px;
            border-radius: 8px;
            font-weight: 500;
        }

        /* قائمة التوقعات المرتبة من الأكبر للأصغر */
        .section-title {
            font-size: 1.5rem;
            font-weight: 800;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--primary-dark);
        }

        .scenarios-list {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .scenario-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 18px 22px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-right: 6px solid #cbd5e0;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .scenario-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }

        /* تدرج الألوان حسب قوة التوقع */
        .rank-1 { border-right-color: #9b2c2c; } /* أعلى انسحاب */
        .rank-2 { border-right-color: var(--danger); }
        .rank-3 { border-right-color: var(--warning); }
        .rank-4 { border-right-color: #3182ce; }
        .rank-5 { border-right-color: var(--success); } /* أقل انسحاب */

        .scenario-info h4 {
            font-size: 1.15rem;
            margin-bottom: 4px;
        }

        .scenario-info p {
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        .scenario-badge {
            text-align: center;
            min-width: 140px;
        }

        .badge-count {
            font-size: 1.4rem;
            font-weight: 800;
            display: block;
        }

        .badge-tag {
            font-size: 0.75rem;
            padding: 2px 8px;
            border-radius: 20px;
            background: #edf2f7;
            display: inline-block;
            margin-top: 4px;
        }

        footer {
            text-align: center;
            margin-top: 30px;
            color: var(--text-muted);
            font-size: 0.85rem;
        }

        @media (max-width: 600px) {
            header h1 { font-size: 2rem; }
            .scenario-card {
                flex-direction: column;
                align-items: flex-start;
                gap: 12px;
            }
            .scenario-badge {
                text-align: right;
                width: 100%;
                border-top: 1px dashed #e2e8f0;
                padding-top: 8px;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        
        <!-- العنوان العريض المطلوب -->
        <header>
            <h1>تقديم الجامعات السودانيه</h1>
            <p>لوحة مؤشرات وتوقعات انسحاب الطلاب من إجمالي (100) مرشح</p>
        </header>

        <!-- بطاقات عامة -->
        <div class="summary-grid">
            <div class="summary-card">
                <h3>إجمالي المرشحين</h3>
                <div class="number">100</div>
            </div>
            <div class="summary-card">
                <h3>أعلى سيناريو انسحاب</h3>
                <div class="number" style="color: #9b2c2c;">45 - 50</div>
            </div>
            <div class="summary-card">
                <h3>المتوسط المعتاد سنوياً</h3>
                <div class="number" style="color: var(--warning);">20 - 30</div>
            </div>
            <div class="summary-card">
                <h3>أدنى سيناريو انسحاب</h3>
                <div class="number" style="color: var(--success);">5 - 10</div>
            </div>
        </div>

        <!-- أداة تفاعلية سريعة لاختبار أثر الانسحاب -->
        <div class="simulator">
            <h3>محاكي أثر الانسحابات (جرّب بنفسك):</h3>
            <div class="slider-box">
                <input type="range" id="withdrawSlider" min="0" max="100" value="25" oninput="updateSim(this.value)">
                <span class="slider-value" id="withdrawDisplay">25</span>
            </div>
            <div class="calc-result">
                <span>الطلاب المتبقين مؤكداً: <strong id="remStudents" style="color: var(--primary);">75</strong></span>
                <span>المقاعد المتاحة لطلاب البدلاء (قوائم الانتظار): <strong id="vacantSeats" style="color: var(--danger);">25</strong> مقعد</span>
            </div>
        </div>

        <!-- التوقعات مرتبة من الأكبر إلى الأصغر -->
        <h2 class="section-title">
            <span>توقعات نسب الانسحاب (مرتبة تنازلياً من الأكبر للأصغر)</span>
        </h2>

        <div class="scenarios-list">
            
            <!-- 1. أعلى توقع -->
            <div class="scenario-card rank-1">
                <div class="scenario-info">
                    <h4>1. سيناريو الانسحاب الأقصى (الذروة)</h4>
                    <p>يحدث غالباً عند فتح منح خارجية متزامنة، أو صعوبة الرسوم، أو تفضيل تكرار التقديم.</p>
                </div>
                <div class="scenario-badge">
                    <span class="badge-count" style="color: #9b2c2c;">45 - 50 منسحب</span>
                    <span class="badge-tag">أعلى توقع ممكن</span>
                </div>
            </div>

            <!-- 2. توقع مرتفع -->
            <div class="scenario-card rank-2">
                <div class="scenario-info">
                    <h4>2. سيناريو الانسحاب المرتفع</h4>
                    <p>انسحاب نتيجة التحويل لجامعات ولائية، أو القبول في الكليات العسكرية/الخاصة البديلة.</p>
                </div>
                <div class="scenario-badge">
                    <span class="badge-count" style="color: var(--danger);">35 - 44 منسحب</span>
                    <span class="badge-tag">توقع مرتفع</span>
                </div>
            </div>

            <!-- 3. توقع متوسط (الأكثر ترجيحاً) -->
            <div class="scenario-card rank-3">
                <div class="scenario-info">
                    <h4>3. سيناريو المعدل الطبيعي (الأقرب للواقع)</h4>
                    <p>معدل الهجران والانسحاب المعتاد في معظم كليات التعليم العالي بالسودان في الدفعة الأولى.</p>
                </div>
                <div class="scenario-badge">
                    <span class="badge-count" style="color: var(--warning);">20 - 34 منسحب</span>
                    <span class="badge-tag">الأكثر احتمالاً</span>
                </div>
            </div>

            <!-- 4. توقع منخفض -->
            <div class="scenario-card rank-4">
                <div class="scenario-info">
                    <h4>4. سيناريو الاستقرار النسبي</h4>
                    <p>يحدث عندما تكون التخصصات المرشح لها الطلاب ذات رغبة أولى عالية (مثل الطب والهندسة).</p>
                </div>
                <div class="scenario-badge">
                    <span class="badge-count" style="color: #3182ce;">11 - 19 منسحب</span>
                    <span class="badge-tag">توقع منخفض</span>
                </div>
            </div>

            <!-- 5. أدنى توقع -->
            <div class="scenario-card rank-5">
                <div class="scenario-info">
                    <h4>5. سيناريو الانسحاب الأدنى (أعلى نسبة التزام)</h4>
                    <p>التزام شبه كامل بالمقاعد مع انسحابات نادرة فقط لأسباب وظروف قاهرة.</p>
                </div>
                <div class="scenario-badge">
                    <span class="badge-count" style="color: var(--success);">1 - 10 منسحب</span>
                    <span class="badge-tag">أدنى توقع</span>
                </div>
            </div>

        </div>

        <footer>
            منظومة توقعات القبول والانسحاب الميداني - تقديم الجامعات السودانية
        </footer>

    </div>

    <script>
        function updateSim(val) {
            const total = 100;
            const withdraw = parseInt(val);
            document.getElementById('withdrawDisplay').innerText = withdraw;
            document.getElementById('remStudents').innerText = total - withdraw;
            document.getElementById('vacantSeats').innerText = withdraw;
        }
    </script>
</body>
</html>
