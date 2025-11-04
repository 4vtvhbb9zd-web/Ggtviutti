# Ggtviutti
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار المول - الكيمياء</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #8B6B4D 0%, #D7B899 100%);
            color: #5D4037;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background-color: rgba(255, 248, 240, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(139, 107, 77, 0.3);
            overflow: hidden;
            border: 2px solid #A1887F;
        }
        
        header {
            background: linear-gradient(90deg, #6D4C41, #8D6E63);
            color: #FFECB3;
            padding: 25px;
            text-align: center;
            border-bottom: 5px solid #5D4037;
            position: relative;
            overflow: hidden;
        }
        
        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100" opacity="0.1"><path d="M10,10 L90,10 L90,90 L10,90 Z" stroke="%23FFECB3" fill="none" stroke-width="2"/></svg>');
            background-size: 50px 50px;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .content {
            display: flex;
            flex-wrap: wrap;
        }
        
        .video-section {
            flex: 1;
            min-width: 300px;
            padding: 20px;
            background-color: #EFEBE9;
            border-left: 1px solid #D7CCC8;
        }
        
        .quiz-section {
            flex: 2;
            min-width: 300px;
            padding: 20px;
        }
        
        .video-container {
            background: #8D6E63;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            color: #FFECB3;
            text-align: center;
            border: 2px solid #5D4037;
        }
        
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            overflow: hidden;
            border-radius: 8px;
            margin: 15px 0;
            border: 2px solid #5D4037;
        }
        
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        
        .lesson-content {
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(139, 107, 77, 0.2);
            margin-top: 15px;
            border: 1px solid #D7CCC8;
        }
        
        .question {
            background: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(139, 107, 77, 0.2);
            display: none;
            border: 1px solid #D7CCC8;
        }
        
        .question.active {
            display: block;
        }
        
        .question-number {
            font-weight: bold;
            color: #5D4037;
            margin-bottom: 10px;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
        }
        
        .question-text {
            font-size: 1.1rem;
            margin-bottom: 20px;
            color: #5D4037;
            line-height: 1.8;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .option {
            padding: 12px 15px;
            background: #F5F5F5;
            border: 2px solid #D7CCC8;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .option:hover {
            background: #E0E0E0;
            border-color: #8D6E63;
        }
        
        .option.correct {
            background: #E8F5E9;
            border-color: #4CAF50;
            color: #2E7D32;
        }
        
        .option.incorrect {
            background: #FFEBEE;
            border-color: #F44336;
            color: #C62828;
        }
        
        .explanation {
            margin-top: 15px;
            padding: 15px;
            border-radius: 8px;
            display: none;
        }
        
        .explanation.correct {
            background: #E8F5E9;
            border-left: 5px solid #4CAF50;
            display: block;
        }
        
        .explanation.incorrect {
            background: #FFEBEE;
            border-left: 5px solid #F44336;
            display: block;
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        button {
            padding: 12px 25px;
            background: #8D6E63;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background 0.3s;
            border: 1px solid #5D4037;
            font-weight: bold;
        }
        
        button:hover {
            background: #6D4C41;
        }
        
        button:disabled {
            background: #BCAAA4;
            cursor: not-allowed;
        }
        
        .results {
            text-align: center;
            padding: 30px;
            display: none;
        }
        
        .results.active {
            display: block;
        }
        
        .score {
            font-size: 2.5rem;
            font-weight: bold;
            color: #5D4037;
            margin: 20px 0;
        }
        
        .percentage {
            font-size: 1.5rem;
            color: #8D6E63;
            margin-bottom: 20px;
        }
        
        .progress-bar {
            height: 10px;
            background: #D7CCC8;
            border-radius: 5px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: #8D6E63;
            width: 0%;
            transition: width 0.5s;
        }
        
        .summary {
            margin-top: 20px;
            text-align: right;
            background: #F5F5F5;
            padding: 20px;
            border-radius: 10px;
            border: 1px solid #D7CCC8;
        }
        
        .retry-btn {
            background: #5D4037;
            margin-top: 20px;
            padding: 15px 40px;
            font-size: 1.2rem;
        }
        
        .retry-btn:hover {
            background: #3E2723;
        }
        
        .student-grade {
            margin: 25px 0;
            padding: 20px;
            background: linear-gradient(135deg, #F5F5F5, #E0E0E0);
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(139, 107, 77, 0.2);
            border: 1px solid #D7CCC8;
        }
        
        .grade-circle {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: #8D6E63;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2.5rem;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(93, 64, 55, 0.4);
            border: 3px solid #5D4037;
        }
        
        .grade-text {
            margin-top: 15px;
            font-size: 1.3rem;
            color: #5D4037;
            font-weight: bold;
        }
        
        .student-info {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(139, 107, 77, 0.2);
            margin-bottom: 20px;
            text-align: center;
            border: 1px solid #D7CCC8;
        }
        
        .student-info h2 {
            color: #5D4037;
            margin-bottom: 20px;
        }
        
        .form-group {
            margin-bottom: 20px;
            text-align: right;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #5D4037;
        }
        
        .form-group input, .form-group select {
            width: 100%;
            padding: 12px;
            border: 2px solid #D7CCC8;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
            background: #FFF8F0;
        }
        
        .form-group input:focus, .form-group select:focus {
            border-color: #8D6E63;
            outline: none;
        }
        
        .start-btn {
            background: #5D4037;
            font-size: 1.2rem;
            padding: 15px 40px;
        }
        
        .start-btn:hover {
            background: #3E2723;
        }
        
        .student-details {
            background: #F5F5F5;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            border-right: 5px solid #8D6E63;
            border: 1px solid #D7CCC8;
        }
        
        .student-details h3 {
            color: #5D4037;
            margin-bottom: 10px;
        }
        
        .final-percentage {
            font-size: 3rem;
            font-weight: bold;
            color: #5D4037;
            margin: 20px 0;
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .final-grade {
            font-size: 2rem;
            color: #8D6E63;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
        }
        
        .question-indicators {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
            justify-content: center;
            padding: 15px;
            background: #F5F5F5;
            border-radius: 10px;
            border: 1px solid #D7CCC8;
        }
        
        .question-indicator {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid #5D4037;
            background: #FFF8F0;
            color: #5D4037;
        }
        
        .question-indicator.current {
            background: #8D6E63;
            color: white;
            transform: scale(1.1);
        }
        
        .question-indicator.answered {
            background: #4CAF50;
            color: white;
        }
        
        .question-indicator.incorrect {
            background: #F44336;
            color: white;
        }
        
        .question-indicator.unanswered {
            background: #9E9E9E;
            color: white;
        }
        
        .lesson-content ul {
            padding-right: 20px;
            margin-top: 10px;
        }
        
        .lesson-content li {
            margin-bottom: 10px;
            line-height: 1.6;
        }
        
        /* إضافة قسم الإحصائيات */
        .statistics {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(139, 107, 77, 0.2);
            text-align: center;
            border: 1px solid #D7CCC8;
        }
        
        .stat-card i {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #8D6E63;
        }
        
        .stat-card h3 {
            color: #5D4037;
            margin-bottom: 10px;
        }
        
        .stat-card .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: #8D6E63;
        }
        
        .stat-card .stat-label {
            color: #795548;
            font-size: 0.9rem;
        }
        
        .performance-chart {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(139, 107, 77, 0.2);
            margin: 20px 0;
            border: 1px solid #D7CCC8;
        }
        
        .performance-chart h3 {
            color: #5D4037;
            margin-bottom: 15px;
            text-align: center;
        }
        
        .chart-bars {
            display: flex;
            align-items: flex-end;
            justify-content: space-around;
            height: 200px;
            margin-top: 20px;
        }
        
        .chart-bar {
            width: 40px;
            background: #8D6E63;
            border-radius: 5px 5px 0 0;
            position: relative;
            transition: height 0.5s;
        }
        
        .chart-bar.correct {
            background: #4CAF50;
        }
        
        .chart-bar.incorrect {
            background: #F44336;
        }
        
        .chart-bar-label {
            position: absolute;
            bottom: -25px;
            left: 0;
            right: 0;
            text-align: center;
            font-size: 0.8rem;
            color: #5D4037;
        }
        
        .chart-bar-value {
            position: absolute;
            top: -25px;
            left: 0;
            right: 0;
            text-align: center;
            font-weight: bold;
            color: #5D4037;
        }
        
        .time-stats {
            display: flex;
            justify-content: space-around;
            margin: 20px 0;
        }
        
        .time-stat {
            text-align: center;
        }
        
        .time-stat-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #8D6E63;
        }
        
        .time-stat-label {
            color: #795548;
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }
            
            .video-section {
                border-left: none;
                border-bottom: 1px solid #D7CCC8;
            }
            
            .grade-circle {
                width: 120px;
                height: 120px;
                font-size: 2rem;
            }
            
            .final-percentage {
                font-size: 2.5rem;
            }
            
            .final-grade {
                font-size: 1.5rem;
            }
            
            .question-indicator {
                width: 35px;
                height: 35px;
                font-size: 0.9rem;
            }
            
            .statistics {
                grid-template-columns: 1fr;
            }
            
            .chart-bars {
                height: 150px;
            }
            
            .chart-bar {
                width: 30px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-flask"></i> اختبار الكيمياء - درس المول</h1>
            <p class="subtitle">اختبر معرفتك في مفهوم المول والكتلة المولية وعدد أفوجادرو</p>
        </header>
        
        <div class="content">
            <div class="quiz-section">
                <!-- قسم إدخال بيانات الطالب -->
                <div id="student-form" class="student-info">
                    <h2>بيانات الطالب</h2>
                    <div class="form-group">
                        <label for="student-name">اسم الطالب:</label>
                        <input type="text" id="student-name" placeholder="أدخل اسمك الكامل">
                    </div>
                    <div class="form-group">
                        <label for="student-class">اختر الشعبة:</label>
                        <select id="student-class">
                            <option value="">-- اختر الشعبة --</option>
                            <option value="1">الشعبة 1</option>
                            <option value="2">الشعبة 2</option>
                            <option value="3">الشعبة 3</option>
                            <option value="4">الشعبة 4</option>
                            <option value="5">الشعبة 5</option>
                            <option value="6">الشعبة 6</option>
                            <option value="7">الشعبة 7</option>
                        </select>
                    </div>
                    <button id="start-btn" class="start-btn">بدء الاختبار</button>
                </div>
                
                <!-- قسم عرض بيانات الطالب -->
                <div id="student-display" class="student-details" style="display: none;">
                    <h3 id="display-name"></h3>
                    <p id="display-class"></p>
                </div>
                
                <!-- مؤشرات الأسئلة -->
                <div id="question-indicators" class="question-indicators" style="display: none;">
                    <!-- سيتم إضافة دوائر الأسئلة هنا ديناميكيًا -->
                </div>
                
                <!-- قسم الأسئلة -->
                <div id="question-container">
                    <!-- الأسئلة سيتم إضافتها هنا ديناميكيًا -->
                </div>
                
                <div class="navigation">
                    <button id="prev-btn" disabled>السؤال السابق</button>
                    <button id="next-btn" disabled>السؤال التالي</button>
                </div>
                
                <!-- قسم النتائج -->
                <div id="results" class="results">
                    <h2>نتيجة الاختبار</h2>
                    
                    <div class="student-details">
                        <h3 id="result-name"></h3>
                        <p id="result-class"></p>
                    </div>
                    
                    <div class="final-percentage" id="final-percentage">0%</div>
                    <div class="final-grade" id="final-grade">ضعيف</div>
                    
                    <div class="student-grade">
                        <div class="grade-circle" id="grade-circle">0%</div>
                        <div class="grade-text" id="grade-text">ضعيف</div>
                    </div>
                    
                    <div class="score">لقد أجبت على <span id="correct-answers">0</span> من أصل 50 سؤالاً بشكل صحيح</div>
                    <div class="percentage">النسبة المئوية: <span id="percentage">0%</span></div>
                    
                    <div class="progress-bar">
                        <div class="progress" id="progress-bar"></div>
                    </div>
                    
                    <!-- قسم الإحصائيات -->
                    <div class="statistics">
                        <div class="stat-card">
                            <i class="fas fa-check-circle"></i>
                            <h3>الإجابات الصحيحة</h3>
                            <div class="stat-value" id="stat-correct">0</div>
                            <div class="stat-label">سؤال</div>
                        </div>
                        
                        <div class="stat-card">
                            <i class="fas fa-times-circle"></i>
                            <h3>الإجابات الخاطئة</h3>
                            <div class="stat-value" id="stat-incorrect">0</div>
                            <div class="stat-label">سؤال</div>
                        </div>
                        
                        <div class="stat-card">
                            <i class="fas fa-chart-line"></i>
                            <h3>معدل النجاح</h3>
                            <div class="stat-value" id="stat-success-rate">0%</div>
                            <div class="stat-label">من إجمالي الأسئلة</div>
                        </div>
                        
                        <div class="stat-card">
                            <i class="fas fa-trophy"></i>
                            <h3>الترتيب</h3>
                            <div class="stat-value" id="stat-rank">-</div>
                            <div class="stat-label">من حيث الأداء</div>
                        </div>
                    </div>
                    
                    <!-- مخطط الأداء -->
                    <div class="performance-chart">
                        <h3>مخطط الأداء</h3>
                        <div class="chart-bars" id="performance-chart">
                            <!-- سيتم إضافة الأعمدة هنا ديناميكيًا -->
                        </div>
                    </div>
                    
                    <!-- إحصائيات الوقت -->
                    <div class="time-stats">
                        <div class="time-stat">
                            <div class="time-stat-value" id="time-taken">0:00</div>
                            <div class="time-stat-label">الوقت المستغرق</div>
                        </div>
                        
                        <div class="time-stat">
                            <div class="time-stat-value" id="average-time">0:00</div>
                            <div class="time-stat-label">متوسط الوقت للسؤال</div>
                        </div>
                    </div>
                    
                    <div class="summary" id="summary">
                        <!-- الملخص سيتم إضافته هنا -->
                    </div>
                    
                    <button class="retry-btn" id="retry-btn"><i class="fas fa-redo"></i> إعادة الاختبار</button>
                </div>
            </div>
            
            <div class="video-section">
                <div class="video-container">
                    <h3>شرح درس المول</h3>
                    <div class="video-wrapper">
                        <!-- تحديث رابط الفيديو إلى الرابط المطلوب -->
                        <iframe src="https://www.youtube.com/embed/8s45w1twUkE" 
                                title="شرح درس المول" 
                                frameborder="0" 
                                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                                allowfullscreen>
                        </iframe>
                    </div>
                    <p>شاهد هذا الفيديو لمراجعة مفهوم المول قبل البدء بالاختبار</p>
                </div>
                
                <div class="lesson-content">
                    <h3>معلومات عن المول</h3>
                    <ul>
                        <li>المول هو وحدة قياس كمية المادة في النظام الدولي للوحدات</li>
                        <li>عدد أفوجادرو = \( 6.02 \times 10^{23} \) جسيم/مول</li>
                        <li>الكتلة المولية = كتلة مول واحد من المادة (g/mol)</li>
                        <li>لتحويل المولات إلى جسيمات: عدد الجسيمات = عدد المولات × عدد أفوجادرو</li>
                        <li>لتحويل الكتلة إلى مولات: عدد المولات = الكتلة ÷ الكتلة المولية</li>
                        <li>المول الواحد من أي غاز في الظروف القياسية يحتل حجم 22.4 لتر</li>
                        <li>الكتلة المولية للماء H₂O = 18 g/mol</li>
                        <li>الكتلة المولية لثاني أكسيد الكربون CO₂ = 44 g/mol</li>
                        <li>الكتلة المولية لكلوريد الصوديوم NaCl = 58.5 g/mol</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>

    <script>
        // بيانات الأسئلة (50 سؤالاً)
        const questions = [
            {
                question: "ما قيمة عدد أفوجادرو؟",
                options: ["6.02 × 10²²", "6.02 × 10²³", "6.02 × 10²⁴"],
                correct: 1,
                explanation: "عدد أفوجادرو يساوي 6.02 × 10²³ وهو عدد الجسيمات في المول الواحد من أي مادة."
            },
            {
                question: "المول هو وحدة قياس:",
                options: ["الكتلة", "الحجم", "كمية المادة"],
                correct: 2,
                explanation: "المول هو الوحدة الأساسية في النظام الدولي للوحدات لقياس كمية المادة."
            },
            // ... (نفس الأسئلة السابقة)
        ];

        // تهيئة المتغيرات
        let currentQuestion = 0;
        let userAnswers = new Array(questions.length).fill(null);
        let score = 0;
        let studentName = "";
        let studentClass = "";
        let shuffledQuestions = [];
        let startTime, endTime;

        // عناصر DOM
        const studentForm = document.getElementById('student-form');
        const studentDisplay = document.getElementById('student-display');
        const displayName = document.getElementById('display-name');
        const displayClass = document.getElementById('display-class');
        const questionContainer = document.getElementById('question-container');
        const questionIndicators = document.getElementById('question-indicators');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const resultsContainer = document.getElementById('results');
        const resultName = document.getElementById('result-name');
        const resultClass = document.getElementById('result-class');
        const correctAnswersSpan = document.getElementById('correct-answers');
        const percentageSpan = document.getElementById('percentage');
        const finalPercentage = document.getElementById('final-percentage');
        const finalGrade = document.getElementById('final-grade');
        const progressBar = document.getElementById('progress-bar');
        const summaryDiv = document.getElementById('summary');
        const retryBtn = document.getElementById('retry-btn');
        const gradeCircle = document.getElementById('grade-circle');
        const gradeText = document.getElementById('grade-text');
        const startBtn = document.getElementById('start-btn');
        const studentNameInput = document.getElementById('student-name');
        const studentClassInput = document.getElementById('student-class');
        
        // عناصر الإحصائيات
        const statCorrect = document.getElementById('stat-correct');
        const statIncorrect = document.getElementById('stat-incorrect');
        const statSuccessRate = document.getElementById('stat-success-rate');
        const statRank = document.getElementById('stat-rank');
        const performanceChart = document.getElementById('performance-chart');
        const timeTaken = document.getElementById('time-taken');
        const averageTime = document.getElementById('average-time');

        // بدء الاختبار بعد إدخال البيانات
        startBtn.addEventListener('click', function() {
            if (studentNameInput.value.trim() === "" || studentClassInput.value === "") {
                alert("يرجى إدخال اسم الطالب واختيار الشعبة");
                return;
            }
            
            studentName = studentNameInput.value.trim();
            studentClass = studentClassInput.options[studentClassInput.selectedIndex].text;
            
            studentForm.style.display = 'none';
            studentDisplay.style.display = 'block';
            questionIndicators.style.display = 'flex';
            displayName.textContent = `الطالب: ${studentName}`;
            displayClass.textContent = `الشعبة: ${studentClass}`;
            
            // خلط الأسئلة عشوائياً
            shuffledQuestions = [...questions];
            shuffleArray(shuffledQuestions);
            
            // تسجيل وقت البدء
            startTime = new Date();
            
            initQuiz();
        });

        // دالة لخلط الأسئلة عشوائياً
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        // تهيئة الاختبار
        function initQuiz() {
            createQuestionIndicators();
            showQuestion(currentQuestion);
            updateNavigation();
        }

        // إنشاء دوائر مؤشرات الأسئلة
        function createQuestionIndicators() {
            questionIndicators.innerHTML = '';
            
            for (let i = 0; i < shuffledQuestions.length; i++) {
                const indicator = document.createElement('div');
                indicator.className = 'question-indicator';
                indicator.textContent = i + 1;
                indicator.addEventListener('click', () => {
                    // لا يمكن الانتقال لسؤال لم يتم الإجابة عليه بعد
                    if (userAnswers[i] !== null) {
                        currentQuestion = i;
                        showQuestion(currentQuestion);
                        updateNavigation();
                    }
                });
                
                questionIndicators.appendChild(indicator);
            }
            
            updateQuestionIndicators();
        }

        // تحديث دوائر مؤشرات الأسئلة
        function updateQuestionIndicators() {
            const indicators = document.querySelectorAll('.question-indicator');
            
            indicators.forEach((indicator, index) => {
                // إزالة جميع الفئات
                indicator.classList.remove('current', 'answered', 'incorrect', 'unanswered');
                
                // إضافة الفئة المناسبة
                if (index === currentQuestion) {
                    indicator.classList.add('current');
                } else if (userAnswers[index] !== null) {
                    if (userAnswers[index] === shuffledQuestions[index].correct) {
                        indicator.classList.add('answered');
                    } else {
                        indicator.classList.add('incorrect');
                    }
                } else {
                    indicator.classList.add('unanswered');
                }
            });
        }

        // عرض السؤال الحالي
        function showQuestion(index) {
            questionContainer.innerHTML = '';
            
            const question = shuffledQuestions[index];
            const questionElement = document.createElement('div');
            questionElement.className = 'question active';
            
            let optionsHTML = '';
            question.options.forEach((option, i) => {
                const isSelected = userAnswers[index] === i;
                const isCorrect = userAnswers[index] !== null && i === question.correct;
                const isIncorrect = userAnswers[index] !== null && userAnswers[index] === i && userAnswers[index] !== question.correct;
                
                let optionClass = 'option';
                if (isCorrect) optionClass += ' correct';
                if (isIncorrect) optionClass += ' incorrect';
                
                optionsHTML += `
                    <div class="${optionClass}" onclick="selectOption(${i})">
                        ${option}
                    </div>
                `;
            });
            
            questionElement.innerHTML = `
                <div class="question-number">السؤال ${index + 1} من ${shuffledQuestions.length}</div>
                <div class="question-text">${question.question}</div>
                <div class="options">${optionsHTML}</div>
                ${userAnswers[index] !== null ? `
                    <div class="explanation ${userAnswers[index] === question.correct ? 'correct' : 'incorrect'}">
                        ${question.explanation}
                    </div>
                ` : ''}
            `;
            
            questionContainer.appendChild(questionElement);
            updateQuestionIndicators();
        }

        // تحديد خيار
        function selectOption(optionIndex) {
            if (userAnswers[currentQuestion] !== null) return;
            
            userAnswers[currentQuestion] = optionIndex;
            showQuestion(currentQuestion);
            updateNavigation();
        }

        // تحديث أزرار التنقل
        function updateNavigation() {
            // تعطيل زر السابق تماماً (لا يمكن الرجوع للخلف)
            prevBtn.disabled = true;
            
            // تمكين زر التالي فقط إذا تم الإجابة على السؤال الحالي
            nextBtn.disabled = userAnswers[currentQuestion] === null;
            
            if (currentQuestion === shuffledQuestions.length - 1) {
                nextBtn.textContent = 'عرض النتائج';
            } else {
                nextBtn.textContent = 'السؤال التالي';
            }
        }

        // الانتقال إلى السؤال التالي
        function nextQuestion() {
            if (currentQuestion < shuffledQuestions.length - 1) {
                currentQuestion++;
                showQuestion(currentQuestion);
                updateNavigation();
            } else {
                showResults();
            }
        }

        // الانتقال إلى السؤال السابق (معطل)
        function prevQuestion() {
            // لا يمكن الرجوع للخلف
            return;
        }

        // حساب النتيجة وتحديد التقدير
        function calculateScore() {
            score = 0;
            for (let i = 0; i < shuffledQuestions.length; i++) {
                if (userAnswers[i] === shuffledQuestions[i].correct) {
                    score++;
                }
            }
            
            const percentage = Math.round((score / shuffledQuestions.length) * 100);
            
            correctAnswersSpan.textContent = score;
            percentageSpan.textContent = `${percentage}%`;
            finalPercentage.textContent = `${percentage}%`;
            progressBar.style.width = `${percentage}%`;
            gradeCircle.textContent = `${percentage}%`;
            
            // تحديث الإحصائيات
            updateStatistics(percentage, score);
            
            // تحديد التقدير بناءً على النسبة
            let grade, color;
            if (percentage >= 90) {
                grade = "ممتاز";
                color = "#4CAF50";
            } else if (percentage >= 80) {
                grade = "جيد جداً";
                color = "#8BC34A";
            } else if (percentage >= 70) {
                grade = "جيد";
                color = "#FFC107";
            } else if (percentage >= 60) {
                grade = "مقبول";
                color = "#FF9800";
            } else {
                grade = "ضعيف";
                color = "#F44336";
            }
            
            gradeText.textContent = grade;
            finalGrade.textContent = grade;
            gradeCircle.style.background = color;
            
            // إضافة ملخص
            let summaryHTML = '<h3>ملخص الأداء:</h3><ul>';
            
            if (percentage >= 90) {
                summaryHTML += '<li>أداء ممتاز! لديك فهم قوي لمفهوم المول.</li>';
            } else if (percentage >= 70) {
                summaryHTML += '<li>أداء جيد، لكن يمكنك تحسين فهمك بمراجعة بعض النقاط.</li>';
            } else if (percentage >= 50) {
                summaryHTML += '<li>أداء مقبول، ننصحك بمراجعة درس المول مرة أخرى.</li>';
            } else {
                summaryHTML += '<li>تحتاج إلى مراجعة شاملة لدرس المول.</li>';
            }
            
            summaryHTML += `<li>عدد الإجابات الصحيحة: ${score}</li>`;
            summaryHTML += `<li>عدد الإجابات الخاطئة: ${shuffledQuestions.length - score}</li>`;
            summaryHTML += `<li>نسبة النجاح: ${percentage}%</li>`;
            summaryHTML += `<li>التقدير: ${grade}</li>`;
            summaryHTML += '</ul>';
            
            summaryDiv.innerHTML = summaryHTML;
            
            // عرض بيانات الطالب في النتائج
            resultName.textContent = `الطالب: ${studentName}`;
            resultClass.textContent = `الشعبة: ${studentClass}`;
        }

        // تحديث الإحصائيات
        function updateStatistics(percentage, correctAnswers) {
            const incorrectAnswers = shuffledQuestions.length - correctAnswers;
            const successRate = percentage;
            
            // تحديث الإحصائيات الأساسية
            statCorrect.textContent = correctAnswers;
            statIncorrect.textContent = incorrectAnswers;
            statSuccessRate.textContent = `${successRate}%`;
            
            // تحديد الترتيب
            let rank;
            if (percentage >= 90) rank = "ممتاز";
            else if (percentage >= 80) rank = "جيد جداً";
            else if (percentage >= 70) rank = "جيد";
            else if (percentage >= 60) rank = "مقبول";
            else rank = "يحتاج تحسين";
            
            statRank.textContent = rank;
            
            // إنشاء مخطط الأداء
            createPerformanceChart(correctAnswers, incorrectAnswers);
            
            // حساب الوقت المستغرق
            endTime = new Date();
            const timeDiff = endTime - startTime; // بالمللي ثانية
            const minutes = Math.floor(timeDiff / 60000);
            const seconds = Math.floor((timeDiff % 60000) / 1000);
            
            timeTaken.textContent = `${minutes}:${seconds.toString().padStart(2, '0')}`;
            
            // حساب متوسط الوقت لكل سؤال
            const avgTime = timeDiff / shuffledQuestions.length / 1000; // بالثواني
            const avgMinutes = Math.floor(avgTime / 60);
            const avgSeconds = Math.floor(avgTime % 60);
            
            averageTime.textContent = `${avgMinutes}:${avgSeconds.toString().padStart(2, '0')}`;
        }

        // إنشاء مخطط الأداء
        function createPerformanceChart(correct, incorrect) {
            performanceChart.innerHTML = '';
            
            const total = correct + incorrect;
            const correctPercentage = Math.round((correct / total) * 100);
            const incorrectPercentage = Math.round((incorrect / total) * 100);
            
            // إنشاء عمود الإجابات الصحيحة
            const correctBar = document.createElement('div');
            correctBar.className = 'chart-bar correct';
            correctBar.style.height = `${correctPercentage}%`;
            correctBar.innerHTML = `
                <div class="chart-bar-value">${correct}</div>
                <div class="chart-bar-label">صحيحة</div>
            `;
            performanceChart.appendChild(correctBar);
            
            // إنشاء عمود الإجابات الخاطئة
            const incorrectBar = document.createElement('div');
            incorrectBar.className = 'chart-bar incorrect';
            incorrectBar.style.height = `${incorrectPercentage}%`;
            incorrectBar.innerHTML = `
                <div class="chart-bar-value">${incorrect}</div>
                <div class="chart-bar-label">خاطئة</div>
            `;
            performanceChart.appendChild(incorrectBar);
        }

        // عرض النتائج
        function showResults() {
            calculateScore();
            document.querySelector('.quiz-section').style.display = 'none';
            resultsContainer.classList.add('active');
        }

        // إعادة الاختبار
        function retryQuiz() {
            currentQuestion = 0;
            userAnswers = new Array(questions.length).fill(null);
            score = 0;
            
            document.querySelector('.quiz-section').style.display = 'block';
            resultsContainer.classList.remove('active');
            studentForm.style.display = 'block';
            studentDisplay.style.display = 'none';
            questionIndicators.style.display = 'none';
            
            // إعادة تعيين حقول الإدخال
            studentNameInput.value = "";
            studentClassInput.selectedIndex = 0;
        }

        // إضافة المستمعين للأحداث
        prevBtn.addEventListener('click', prevQuestion);
        nextBtn.addEventListener('click', nextQuestion);
        retryBtn.addEventListener('click', retryQuiz);

        // جعل الدوال متاحة عالمياً
        window.selectOption = selectOption;
    </script>
</body>
</html>
