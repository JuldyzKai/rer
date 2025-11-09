<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Қазақ жыраулары туралы тест</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 25px;
            text-align: center;
        }
        
        h1 {
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 16px;
            opacity: 0.9;
        }
        
        .progress-container {
            background-color: #f0f0f0;
            height: 8px;
            width: 100%;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #4CAF50, #8BC34A);
            width: 0%;
            transition: width 0.5s ease;
        }
        
        .question-container {
            padding: 30px;
        }
        
        .question-number {
            font-size: 18px;
            color: #2a5298;
            margin-bottom: 10px;
            font-weight: bold;
        }
        
        .question-text {
            font-size: 20px;
            margin-bottom: 25px;
            line-height: 1.5;
            color: #333;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 30px;
        }
        
        .option {
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 16px;
        }
        
        .option:hover {
            background-color: #f5f7fa;
            border-color: #c3cfe2;
        }
        
        .option.selected {
            border-color: #4CAF50;
            background-color: #E8F5E9;
        }
        
        .option.correct {
            border-color: #4CAF50;
            background-color: #E8F5E9;
        }
        
        .option.incorrect {
            border-color: #F44336;
            background-color: #FFEBEE;
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
        }
        
        button {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        
        #prev-btn {
            background-color: #f0f0f0;
            color: #333;
        }
        
        #prev-btn:hover:not(:disabled) {
            background-color: #e0e0e0;
        }
        
        #next-btn, #submit-btn {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
        }
        
        #next-btn:hover, #submit-btn:hover {
            background: linear-gradient(135deg, #2a5298 0%, #1e3c72 100%);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none !important;
            box-shadow: none !important;
        }
        
        .result-container {
            padding: 30px;
            text-align: center;
            display: none;
        }
        
        .result-title {
            font-size: 28px;
            margin-bottom: 20px;
            color: #2a5298;
        }
        
        .score {
            font-size: 72px;
            font-weight: bold;
            color: #4CAF50;
            margin: 20px 0;
        }
        
        .score-text {
            font-size: 20px;
            margin-bottom: 30px;
            color: #555;
        }
        
        .restart-btn {
            background: linear-gradient(135deg, #4CAF50, #8BC34A);
            color: white;
            padding: 15px 30px;
            font-size: 18px;
            border-radius: 10px;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .restart-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        .feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            display: none;
        }
        
        .feedback.correct {
            background-color: #E8F5E9;
            color: #2E7D32;
            border: 1px solid #4CAF50;
        }
        
        .feedback.incorrect {
            background-color: #FFEBEE;
            color: #C62828;
            border: 1px solid #F44336;
        }
        
        @media (max-width: 600px) {
            .container {
                border-radius: 10px;
            }
            
            header {
                padding: 20px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .question-container {
                padding: 20px;
            }
            
            .question-text {
                font-size: 18px;
            }
            
            button {
                padding: 10px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Қазақ жыраулары туралы тест</h1>
            <div class="subtitle">35 сұрақтық тапсырыс</div>
        </header>
        
        <div class="progress-container">
            <div class="progress-bar" id="progress-bar"></div>
        </div>
        
        <div class="question-container" id="question-container">
            <div class="question-number" id="question-number">1-сұрақ / 35</div>
            <div class="question-text" id="question-text"></div>
            
            <div class="options" id="options-container"></div>
            
            <div class="feedback" id="feedback"></div>
            
            <div class="navigation">
                <button id="prev-btn">Алдыңғы</button>
                <button id="next-btn">Келесі</button>
                <button id="submit-btn" style="display: none;">Нәтижені көру</button>
            </div>
        </div>
        
        <div class="result-container" id="result-container">
            <h2 class="result-title">Тест нәтижесі</h2>
            <div class="score" id="score">0</div>
            <div class="score-text" id="score-text"></div>
            <button class="restart-btn" id="restart-btn">Қайта бастау</button>
        </div>
    </div>

    <script>
        // Тест сұрақтары мен дұрыс жауаптары
        const questions = [
            {
                question: "1. «Еділ бол да, Жайық бол» толғауы неге шақыратынын табыңыз.",
                options: [
                    "A. Қолөнер үйренуге",
                    "B. Оқу-білім игеруге",
                    "C. Аңшылықпен айналысуға",
                    "D. Бірлік-ынтымаққа"
                ],
                correctAnswer: 3
            },
            {
                question: "2. «Ер Шобан» дастаны қай жыраудікі екенін көрсетіңіз.",
                options: [
                    "A. Шалкиіз жыраудікі",
                    "B. Асан қайғынікі",
                    "C. Ақтамберді жыраудікі",
                    "D. Доспамбет жыраудікі"
                ],
                correctAnswer: 0
            },
            {
                question: "3. «Бір жақсымен дос болсаң, Азбас-тозбас мүлкі етер» – деген жолдар қай жыраудың толғауынан алынғанын табыңыз.",
                options: [
                    "A. Ақтамберді жырау толғауынан",
                    "B. Доспамбет жырау толғауынан",
                    "C. Қазтуған жырау толғауынан",
                    "D. Шалкиіз жырау толғауынан"
                ],
                correctAnswer: 3
            },
            {
                question: "4. ХVІ ғасырда өмір сүрген жырауды көрсетіңіз.",
                options: [
                    "A. Асан қайғы",
                    "B. Доспамбет",
                    "C. Қазтуған",
                    "D. Жиембет"
                ],
                correctAnswer: 1
            },
            {
                question: "5. Қазтуған жырау қай ғасырда өмір сүргенін анықтаңыз.",
                options: [
                    "A. XVII ғасырда",
                    "B. XIX ғасырда",
                    "C. XV ғасырда",
                    "D. XX ғасырда"
                ],
                correctAnswer: 2
            },
            {
                question: "6. «Айдаса қойдың көсемі, Сөйлесе қызыл тілдің шешені» деп Қазтуған жырау кім туралы толғағанын табыңыз.",
                options: [
                    "A. Жары туралы",
                    "B. Өзі туралы",
                    "C. Хан туралы",
                    "D. Досы туралы"
                ],
                correctAnswer: 1
            },
            {
                question: "7. ХV ғасырда өмір сүрген жырауларды көрсетіңіз.",
                options: [
                    "A. Ақтамберлі, Доспамбет",
                    "B. Доспамбет, Бұқар",
                    "C. Асан қайғы, Қазтуған",
                    "D. Шалкиіз, Жиембет"
                ],
                correctAnswer: 2
            },
            {
                question: "8. Қазтуған толғауларының негізгі арқауын көрсетіңіз.",
                options: [
                    "A. Оқу-білім, өнер",
                    "B. Береке-бірлік, ынтымақ",
                    "C. Туған елі, кіндік кескен жері",
                    "D. Қолөнер, тігіншілік"
                ],
                correctAnswer: 2
            },
            {
                question: "9. Жорықта оқ тиіп, өлім аузынан қайтқан жырауды көрсетіңіз.",
                options: [
                    "A. Доспамбет",
                    "B. Қазтуған",
                    "C. Ақтамберді",
                    "D. Асан қайғы"
                ],
                correctAnswer: 0
            },
            {
                question: "10. Халқына жайлы қоныс, ырысты жер іздеген жырауды көрсетіңіз.",
                options: [
                    "A. Бұқар жырау",
                    "B. Қазтуған жырау",
                    "C. Шалкиіз жырау",
                    "D. Асан қайғы"
                ],
                correctAnswer: 3
            },
            {
                question: "11. Жыраулар поэзиясының негізгі тақырыбын көрсетіңіз.",
                options: [
                    "A. Достық",
                    "B. Махаббат",
                    "C. Елдің бірлігі, бүтіндігі",
                    "D. Сүйіспеншілік"
                ],
                correctAnswer: 2
            },
            {
                question: "12. Қазтуғанның толғау (-лары)",
                options: [
                    "A. «Мадақ жыры»",
                    "B. «Айналайын, Ақ Жайық»",
                    "C. «Белгілі биік көк сеңгір»",
                    "D. «Алаң да алаң, алаң жұрт»",
                    "E. «Асқар, асқар, асқар тау»",
                    "F. «Зар жылатып момынды»"
                ],
                correctAnswer: [0, 2, 3] // Бірнеше дұрыс жауап
            },
            {
                question: "13. Шалкиіздің шығармасын табыңыз.",
                options: [
                    "A. «Мінкен ер»",
                    "B. «Арғымаққа оқ тиді»",
                    "C. «Тілек»",
                    "D. «Асқар, асқар, асқар тау»"
                ],
                correctAnswer: 3
            },
            {
                question: "14. «Сен алтынсың – мен пұлмын, Сен жібексің – мен жүнмін» – деп толғаған жырауды көрсетіңіз.",
                options: [
                    "A. Шалкиіз",
                    "B. Асан қайғы",
                    "C. Доспамбет",
                    "D. Жиембет"
                ],
                correctAnswer: 0
            },
            {
                question: "15. «Ата жұрты бұқара, Өз қолында болмаса, Қанша жақсы болса да, Қайратты туған ер ғаріп...» шумағының кімнің шығармасынан алынғандығын табыңыз.",
                options: [
                    "A. Үмбетей жыраудан",
                    "B. Жиембет жыраудан",
                    "C. Асан қайғыдан",
                    "D. Шалкиіз жыраудан"
                ],
                correctAnswer: 2
            },
            {
                question: "16. «Шағырмақ бұлт жай тастар» кімнің шығармасы екенін анықтаңыз.",
                options: [
                    "A. Асан қайғы",
                    "B. Қазтуған",
                    "C. Жиембет",
                    "D. Шалкиіз"
                ],
                correctAnswer: 3
            },
            {
                question: "17. «Ашу – дұшпан, артынан Түсіп кетсең қайтесің Түбі терең қуысқа» – деген өлең жолдары қай жыраудікі екенін белгілеңіз.",
                options: [
                    "A. Бұқар",
                    "B. Қазтуған",
                    "C. Шалкиіз",
                    "D. Асан"
                ],
                correctAnswer: 3
            },
            {
                question: "18. Жыраулар поэзиясының негізгі тақырыптары",
                options: [
                    "A. Басқа елдерді басып алуды ұйымдастыру",
                    "B. Елдің бірлігі, бүтіндігі",
                    "C. Ана мен бала арасындағы махаббат",
                    "D. Көрші елдерге жаугершілык жасау",
                    "E. Туған ел және оған деген сүйіспеншілік",
                    "F. Адамгершілік, этика, мораль"
                ],
                correctAnswer: [1, 4, 5] // Бірнеше дұрыс жауап
            },
            {
                question: "19. «Мадақ жыры» кімнің толғауы екенін белгілеңіз.",
                options: [
                    "A. Асан",
                    "B. Шалкиіз",
                    "C. Бұқар",
                    "D. Қазтуған"
                ],
                correctAnswer: 3
            },
            {
                question: "20. «...Алғаш рет қалың ел қамын ойлап күңіренген қария – Асан» деген сөзді айтқан ғалымды көрсетіңіз.",
                options: [
                    "A. Мұхтар Әуезов",
                    "B. Мағжан Жұмабаев",
                    "C. Ахмет Байтұрсынов",
                    "D. Алма Қыраубаева"
                ],
                correctAnswer: 0
            },
            {
                question: "21. Азау қаласында туып, оны Ыстамбұлға теңеген жырауды белгілеңіз.",
                options: [
                    "A. Доспамбет",
                    "B. Асан қайғы",
                    "C. Ақтамберді",
                    "D. Қазтуған"
                ],
                correctAnswer: 0
            },
            {
                question: "22. Асан қайғы қай ханның тұсында өмір сүргенін көрсетіңіз.",
                options: [
                    "A. Есім ханның",
                    "B. Тәуке ханның",
                    "C. Жәңгір ханның",
                    "D. Жәнібек ханның"
                ],
                correctAnswer: 3
            },
            {
                question: "23. Би Темірдің тұсында өмір сүрген жырауды көрсетіңіз.",
                options: [
                    "A. Жиембет",
                    "B. Шалкиіз",
                    "C. Асан қайғы",
                    "D. Доспамбет"
                ],
                correctAnswer: 1
            },
            {
                question: "24. Шалкиіздің «Жебелей жебе жүгірген» толғауы қай жинаққа енгенін анықтаңыз.",
                options: [
                    "A. «Алдаспан»",
                    "B. «Серке»",
                    "C. «Көктем»",
                    "D. «Асау тұлпар»"
                ],
                correctAnswer: 0
            },
            {
                question: "25. Әскербасы болған жырауды белгілеңіз.",
                options: [
                    "A. Шалкиіз",
                    "B. Асан",
                    "C. Қазтуған",
                    "D. Бұқар"
                ],
                correctAnswer: 2
            },
            {
                question: "26. «Көшпенділер философы» атанған жырауды көрсетіңіз.",
                options: [
                    "A. Шалкиіз",
                    "B. Асан",
                    "C. Бұқар",
                    "D. Қазтуған"
                ],
                correctAnswer: 1
            },
            {
                question: "27. «Көлде жүрген қоңыр қаз» толғауы кімдікі екенін көрсетіңіз.",
                options: [
                    "A. Бұқар жыраудікі",
                    "B. Асан қайғынікі",
                    "C. Қазтуған жыраудікі",
                    "D. Шалкиіз жыраудікі"
                ],
                correctAnswer: 1
            },
            {
                question: "28. Қазтуған жыраудың толғауы (-лары)",
                options: [
                    "A. «Салп-салпыншақ анау үш өзен»",
                    "B. «Арғымаққа оқ тиді»",
                    "C. «Алаң да алаң, алаң жұрт»",
                    "D. «Белгілі биік көк сеңгір»",
                    "E. «Тоғай, тоғай, тоғай су»",
                    "F. «Қоғалы көлдер, қом сулар»"
                ],
                correctAnswer: [0, 3, 5] // Бірнеше дұрыс жауап
            },
            {
                question: "29. Бос орынға қажет сөзді көрсетіңіз. Арыстандай екі бұтын алшайтып, Арғымақ __________ өкінбес.",
                options: [
                    "A. Мінген",
                    "B. Қонған",
                    "C. Киген",
                    "D. Ішкен"
                ],
                correctAnswer: 0
            },
            {
                question: "30. Жыраулар поэзиясында қолданылған әдісті белгілеңіз.",
                options: [
                    "A. Синтаксистік параллелизм",
                    "B. Мысқылдау, әжуалау",
                    "C. Ирония, сарказм",
                    "D. Теңеу, салыстыру"
                ],
                correctAnswer: 0
            },
            {
                question: "31. Өлеңнің жалғасын табыңыз. «Бетегелі Сарыарқаның бойында Соғысып ___________»",
                options: [
                    "A. Құштар өкінбес",
                    "B. Киген өкінбес",
                    "C. Өлген өкінбес",
                    "D. Мінген өкінбес"
                ],
                correctAnswer: 2
            },
            {
                question: "32. Қазтуған жырларының негізгі тақырыбы (-тары)",
                options: [
                    "A. Діни-философиялық сарын",
                    "B. Өмір жайлы",
                    "C. Философиялық ой толғау",
                    "D. Адамгершілік жайлы",
                    "E. Жоңғарларға қарсы күрес туралы",
                    "F. Ел мүддесін қорғауға арналған"
                ],
                correctAnswer: 5
            },
            {
                question: "33. Асан қайғының толғауын көрсетіңіз.",
                options: [
                    "A. «Қоғалы көлдер, қом сулар»",
                    "B. «Бұл заманда не ғаріп?»",
                    "C. «Алаң да алаң, алаң жұрт»",
                    "D. «Айналайын, Ақ Жайық»"
                ],
                correctAnswer: 1
            },
            {
                question: "34. Туған Жайығын, бетегелі Сарыарқасын шексіз сүйген, «Айналайын Ақ Жайық» деп толғаған жырауды көрсетіңіз.",
                options: [
                    "A. Ақтамберді",
                    "B. Доспамбет",
                    "C. Асан қайғы",
                    "D. Қазтуған"
                ],
                correctAnswer: 1
            },
            {
                question: "35. Бос орынға қажет сөзді көрсетіңіз. Анамыз біздің ____________ Келіншек болып түскен жұрт.",
                options: [
                    "A. Қарагөз",
                    "B. Айқаған",
                    "C. Қарашаш",
                    "D. Бозтуған"
                ],
                correctAnswer: 3
            }
        ];

        // Айнымалылар
        let currentQuestionIndex = 0;
        let userAnswers = new Array(questions.length).fill(null);
        let score = 0;

        // DOM элементтері
        const questionNumberElement = document.getElementById('question-number');
        const questionTextElement = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options-container');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const submitBtn = document.getElementById('submit-btn');
        const progressBar = document.getElementById('progress-bar');
        const feedbackElement = document.getElementById('feedback');
        const questionContainer = document.getElementById('question-container');
        const resultContainer = document.getElementById('result-container');
        const scoreElement = document.getElementById('score');
        const scoreTextElement = document.getElementById('score-text');
        const restartBtn = document.getElementById('restart-btn');

        // Сұрақты көрсету функциясы
        function displayQuestion() {
            const currentQuestion = questions[currentQuestionIndex];
            
            // Сұрақ нөмірі мен мәтіні
            questionNumberElement.textContent = `${currentQuestionIndex + 1}-сұрақ / ${questions.length}`;
            questionTextElement.textContent = currentQuestion.question;
            
            // Прогресс жолағын жаңарту
            progressBar.style.width = `${((currentQuestionIndex + 1) / questions.length) * 100}%`;
            
            // Нұсқаларды көрсету
            optionsContainer.innerHTML = '';
            currentQuestion.options.forEach((option, index) => {
                const optionElement = document.createElement('div');
                optionElement.classList.add('option');
                
                // Егер жауап берілген болса, түсін белгілеу
                if (userAnswers[currentQuestionIndex] !== null) {
                    if (Array.isArray(currentQuestion.correctAnswer)) {
                        // Бірнеше дұрыс жауап бар жағдай
                        if (currentQuestion.correctAnswer.includes(index)) {
                            optionElement.classList.add('correct');
                        } else if (userAnswers[currentQuestionIndex].includes(index)) {
                            optionElement.classList.add('incorrect');
                        }
                    } else {
                        // Бір дұрыс жауап бар жағдай
                        if (index === currentQuestion.correctAnswer) {
                            optionElement.classList.add('correct');
                        } else if (index === userAnswers[currentQuestionIndex]) {
                            optionElement.classList.add('incorrect');
                        }
                    }
                }
                
                optionElement.textContent = option;
                optionElement.addEventListener('click', () => selectOption(index));
                optionsContainer.appendChild(optionElement);
            });
            
            // Түймелерді жаңарту
            prevBtn.disabled = currentQuestionIndex === 0;
            
            if (currentQuestionIndex === questions.length - 1) {
                nextBtn.style.display = 'none';
                submitBtn.style.display = 'block';
            } else {
                nextBtn.style.display = 'block';
                submitBtn.style.display = 'none';
            }
            
            // Кері байланысты жасыру
            feedbackElement.style.display = 'none';
        }

        // Нұсқаны таңдау функциясы
        function selectOption(optionIndex) {
            const currentQuestion = questions[currentQuestionIndex];
            
            // Егер бірнеше дұрыс жауап бар болса
            if (Array.isArray(currentQuestion.correctAnswer)) {
                if (userAnswers[currentQuestionIndex] === null) {
                    userAnswers[currentQuestionIndex] = [optionIndex];
                } else {
                    // Егер бұрыннан таңдалған болса, оны алып тастау
                    if (userAnswers[currentQuestionIndex].includes(optionIndex)) {
                        userAnswers[currentQuestionIndex] = userAnswers[currentQuestionIndex].filter(i => i !== optionIndex);
                    } else {
                        // Жаңа таңдау қосу
                        userAnswers[currentQuestionIndex].push(optionIndex);
                    }
                }
            } else {
                // Бір дұрыс жауап бар жағдай
                userAnswers[currentQuestionIndex] = optionIndex;
                
                // Жауапты тексеру және кері байланыс беру
                checkAnswer(optionIndex);
            }
            
            displayQuestion();
        }

        // Жауапты тексеру функциясы (тек бір дұрыс жауап бар жағдай үшін)
        function checkAnswer(selectedOption) {
            const currentQuestion = questions[currentQuestionIndex];
            
            // Егер бір дұрыс жауап бар болса
            if (!Array.isArray(currentQuestion.correctAnswer)) {
                if (selectedOption === currentQuestion.correctAnswer) {
                    feedbackElement.textContent = "Дұрыс жауап!";
                    feedbackElement.className = "feedback correct";
                } else {
                    feedbackElement.textContent = "Қате жауап!";
                    feedbackElement.className = "feedback incorrect";
                }
                feedbackElement.style.display = 'block';
            }
        }

        // Келесі сұраққа өту
        nextBtn.addEventListener('click', () => {
            if (currentQuestionIndex < questions.length - 1) {
                currentQuestionIndex++;
                displayQuestion();
            }
        });

        // Алдыңғы сұраққа өту
        prevBtn.addEventListener('click', () => {
            if (currentQuestionIndex > 0) {
                currentQuestionIndex--;
                displayQuestion();
            }
        });

        // Тестті аяқтау
        submitBtn.addEventListener('click', showResults);

        // Тестті қайта бастау
        restartBtn.addEventListener('click', () => {
            currentQuestionIndex = 0;
            userAnswers = new Array(questions.length).fill(null);
            score = 0;
            questionContainer.style.display = 'block';
            resultContainer.style.display = 'none';
            displayQuestion();
        });

        // Нәтижелерді көрсету
        function showResults() {
            // Ұпайларды есептеу
            score = 0;
            userAnswers.forEach((answer, index) => {
                const question = questions[index];
                
                if (Array.isArray(question.correctAnswer)) {
                    // Бірнеше дұрыс жауап бар жағдай
                    if (answer && answer.length === question.correctAnswer.length && 
                        answer.every(val => question.correctAnswer.includes(val))) {
                        score++;
                    }
                } else {
                    // Бір дұрыс жауап бар жағдай
                    if (answer === question.correctAnswer) {
                        score++;
                    }
                }
            });
            
            // Нәтижелерді көрсету
            scoreElement.textContent = score;
            const percentage = (score / questions.length) * 100;
            
            let scoreText = "";
            if (percentage >= 90) {
                scoreText = "Тамаша! Сіз қазақ жырауларын өте жақсы білесіз!";
            } else if (percentage >= 70) {
                scoreText = "Жақсы! Сіздің біліміңіз жеткілікті деуге болады.";
            } else if (percentage >= 50) {
                scoreText = "Орташа. Қазақ жыраулары туралы біліміңізді жетілдіру керек.";
            } else {
                scoreText = "Жеткіліксіз. Қазақ жыраулары туралы көбірек оқып, білім алу керек.";
            }
            
            scoreTextElement.textContent = `${questions.length} сұрақтың ${score} дұрыс жауаптадыңыз. ${scoreText}`;
            
            // Нәтиже бөлімін көрсету
            questionContainer.style.display = 'none';
            resultContainer.style.display = 'block';
        }

        // Бастапқы сұрақты көрсету
        displayQuestion();
    </script>
</body>
</html>
