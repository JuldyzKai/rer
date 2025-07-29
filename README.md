<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Қыз Жібек жыры</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 20px;
            background-image: url('1қ.jpg');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            color: #2e7d32;
            text-align: center;
            font-size: 2.2em;
            margin-bottom: 10px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }
        
        .subtitle {
            text-align: center;
            color: #555;
            margin-bottom: 30px;
            font-size: 1.1em;
        }
        
        .game-area {
            display: flex;
            justify-content: space-between;
            margin-bottom: 30px;
            min-height: 400px;
        }
        
        .column {
            width: 48%;
            padding: 15px;
            border-radius: 10px;
            background-color: rgba(255, 255, 255, 0.7);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        
        .terms-column {
            border: 2px dashed #2e7d32;
        }
        
        .definitions-column {
            border: 2px dashed #1565c0;
        }
        
        .term {
            padding: 12px 15px;
            margin: 10px 0;
            border-radius: 8px;
            font-size: 1em;
            background-color: #e8f5e9;
            border-left: 5px solid #2e7d32;
            color: #1b5e20;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .definition {
            padding: 12px 15px;
            margin: 10px 0;
            border-radius: 8px;
            cursor: grab;
            font-size: 1em;
            transition: all 0.3s ease;
            position: relative;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            background-color: #e3f2fd;
            border-left: 5px solid #1565c0;
            color: #0d47a1;
        }
        
        .definition:hover {
            transform: translateY(-3px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.15);
        }
        
        .definition.dragging {
            opacity: 0.8;
            transform: scale(1.02);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .controls {
            text-align: center;
            margin-top: 20px;
        }
        
        button {
            background-color: #2e7d32;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1em;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            margin: 0 10px;
        }
        
        button:hover {
            background-color: #1b5e20;
            transform: translateY(-2px);
            box-shadow: 0 6px 10px rgba(0,0,0,0.15);
        }
        
        button.secondary {
            background-color: #1565c0;
        }
        
        button.secondary:hover {
            background-color: #0d47a1;
        }
        
        .correct {
            background-color: #c8e6c9;
            border-left: 5px solid #388e3c;
        }
        
        .incorrect {
            background-color: #ffcdd2;
            border-left: 5px solid #d32f2f;
        }
        
        .matched {
            opacity: 0.6;
            cursor: default;
        }
        
        .score-display {
            text-align: center;
            font-size: 1.2em;
            margin: 20px 0;
            color: #2e7d32;
            font-weight: bold;
        }
        
        .quote {
             font-style: italic;
        text-align: center;
        margin: 20px 0;
        padding: 15px;
        background-color: rgba(233, 245, 233, 0.7);
        border-radius: 8px;
        color: #1b5e20;
        border-left: 4px solid #2e7d32;
        white-space: pre-line;
        line-height: 1.8;
        font-family: 'Times New Roman', serif;
    }
    
    .quote div {
        margin: 0.5em 0;
        text-indent: -2em;
        padding-left: 2em;
        }
        
        .answer-key {
            margin-top: 30px;
            padding: 20px;
            background-color: rgba(233, 245, 233, 0.7);
            border-radius: 8px;
            display: none;
        }
        
        .answer-key h3 {
            color: #2e7d32;
            margin-top: 0;
            text-align: center;
        }
        
        .answer-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #ddd;
        }
        
        .answer-term {
            font-weight: bold;
            color: #1b5e20;
        }
        
        .answer-definition {
            color: #0d47a1;
        }
        
        @media (max-width: 768px) {
            .game-area {
                flex-direction: column;
            }
            
            .column {
                width: 100%;
                margin-bottom: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Қыз Жібек жыры бойынша сөздік тапсырмасы</h1>
        
        
        <div class="quote">
            "– Айналайын Төлеген,
Бикешжан бүгін түс көрді,
Түсінде жаман іс көрді.
Астындағы Көкжорға ат
Ер-тоқымсыз бос көрді.
Ел жайлаған Ақжайық,
Жағалай біткен бидайық.
Алдында жанған шырағын
Біреу үрлеп өшіріп,
Көзінен болды сол ғайып.
Тілімді алсаң, жүрмегін,
Айналайын күйеужан,
Құдайға біз де жылайық.
Төлеген сонда сөйлейді:
– Сәлем де, Жібек қорықпасын,
Өліп кетсем артымда Жібекті
Еш жаманға қор қылмас,
Сансызбай атты інім бар.
Елімнің ақын көсемі
Батыр Шеге дер еді,
Ақылға дархан кен еді. Олай-бұлай боп кетсем,
Сансызбайға басшы боп
Еліңізге келеді.
Тірі тұрса жанымыз,
Көктем шағы болғанда,
Қазбенен бірге келем, – деп, –
Не салса да, Құдайым,
Жібекке дұғай сәлем! – деп, –
Енді атына мінеді.

   Әлқисса, бірнеше күн жол жүріп Төлеген аман-есен еліне келеді. Ата-анасы қуанып, той қылады. Жұрт жиылғанда Базарбай баласынан: «Қайда жүріп, не ғып келдің?» – деп сұрады. Төлеген көрген-білгенінің бәрін қалдырмай, жай-мәнісін баян етеді. Ақырында Базарбай: «Қайныңа енді қашан барасың?» – деп сұрады. Төлеген: «Жазғытұры барамын», – деді. Сонда отырып атасы: «Бір тілегім бар, бересің бе?» – деді. Төлеген абайламастан «берем» деп тастады. «Тілегімді берсең, қайныңа жазғытұрым барма, жыл өткізіп, ендігі жылы осы уақытта бар, осыған уәдеңді бер», – деді Базарбай. Төлеген жауап бермеді.
   Базарбай ашуланып, жұртқа баласының қылығын шағып: «Балам тілегімді бермеді, баруына разы емеспін. Біреуің қошамет қылсаңдар, сендерді де тезіме салып, теріс батамды беремін, Төлегеннің кететінін білсеңдер ұстап беріңдер», – деді. Төлегенге ешкім ермейтін болды, кетерін білсе, ұстап беретін болды. Елінің түрі мынадай болған соң, Төлеген атасынан қорқып, сескеніп, киім-кешегін, ер-тұрманын далаға сақтап, Көкжорға атты далаға бағатын болды. Күндердің бір күнінде Көкжорға атқа мініп алып:

«Жібектің ауылы қайдасың?» – деп, 
Жайыққа қарай жөнеді.
Кетіп бара жатқанда
Сансызбай жылап жүгірді
Төлегеннің артынан.
  Әлқисса, сонда Төлеген: «Жеңешеңді әкелуге барамын, жылама», – деп інісін жұбатты.
– Айналайын қарағым,
Жауға барсам, жарағым,
Айналайын, жылама,
Жібек сынды жеңгеңді
Ап келмекке барамын.
Басыма менің түсіп тұр
Ғашықтықтың әуресі.
Айтып кеткен Жібекке
Жақындап қалды уәдесі.
«Тілімді алмай кеттің», – деп,
Бермеді әкем батасын.
Әкемнен қорқып, елімнен
Жалғыз жолдас ермеді. 
Сөзімді тыңда, қарағым
Өзіңді Құдай жеткізсе,
Алып қойдым бәрін де:
Ат-тұрман, сауыт, жарағың.
Олай-бұлай боп кетсем,
Сенен өзге кімім бар,
Алды-артыңа қарағын.
Олай-бұлай боп кетсем,
Асыл туған Жібекті
Еш жаманға қор қылмай,
Өзің бір алып, сүйгейсің.
Сапар шегіп, жол жүрсең,
Жолдасын жауға алдырмас,
Басшы қылғын Шегені.
Бұл сөзді айтып Төлеген
Сансызбайдың бетінен
Үш қайтара сүйеді.
Жайық пен Теңіз арасы
Үш айшылық жол екен.
Үш айшылық жерлердің,
Қырық бес күндік ортасы,
Атырабы шөл екен.
Шөл жазира ішінде
Қособа деген көл екен.
Ұры, кәззап қарақшы
Мекен қылған жер екен.
Атаңа лағынет Бекежан  Қыз Жібектің сыртынан,
Көп ғашықтың бірі екен.
Баяғы алпыс жігіт қасында,
«Төлеген енді келер», – деп,
Қособаның көлінде
Жолын тосып жүр екен.
Алдынан шығып алпыс жау
Төлегенді қамады.
Еркімен аты жеткен соң,
Жау ортаға алады.
Қорамсаққа қол салды,
Бір салғанда мол салды.
Садақты қолға алады,
Толғап тартып қалады.
Жетеуінен өтеді.
Енді оғын алғанша,
Қорамға қолын салғанша,
Атаңа лағынет Бекежан,
Әккі болған сұм екен.
Төлегеннің артында
Алпыс қадам жақындап,
Бір қурайды паналап,
Жеткен екен жағалап,
Төлегенді атқалы
Жақындап келіп тұр екен.
Мылтыққа білте басады,
Аруағы оның асады. Бекежан атқан жалғыз оқ
Маңдайдан келіп ұрады,
Алтынды сүйек Төлеген,
Талықсып аттан құлады.
  Әлқисса, алпыс қарақшы Төлегенді өлтіріп, ат-тонды олжа қылып бөліп алып, жұртқа айтуға қорқып, еліне келіп адамға сездірмей жата береді. Сонымен сегіз жыл өтеді.
  Бекежанның Жібекті өзі алғысы келеді. Бір күні ойлады: «Төлегенді өлтірдім деп Жібекке білдірейін, батырлығымды білген соң Жібек маған тиеді. Кімге тиер дейсің?»
Мұны ойлап Бекежен той қылады,
«Жібекті алайын» деп ой қылады.
Көкжорға атты желдіртіп жетіп келіп
Тұсына кеп Жібектің сөз сұрады.
– Айтамын айт дегеннен, ар ма, Жібек,
Ботасы өлген түйедей зарла, Жібек.
Кеткелі жаман жарың көп жыл болды,
Хабары сол жездемнің бар ма, Жібек?
Жібек:
– Жоқ екен, әй, Бекежан, ақыл-айлаң,
Қанеки құрбы болып тиген пайдаң?
Атаңа алты лағынет, ит қарақшы,
Көкжорға ат астындағы алдың қайдан? Бекежан:
   – Жол тосып Қособада жатып алдым,
   Біреуді мергендікпен атып алдым,
   Өзім батыр болған соң кімді аяйын,
   Өлтіріп Төлегенді, атын алдым.
   Бекежанның бұл сөзі
   Мұңды болған Жібектің
   Өкпесінен ұрады.
   Өксіп-өксіп жылады.
   Керегені құшақтап,
   Етпетінен құлады.
Жібек:
   – Атаңа лағынет, Бекежан,
   Көрсетпе маған түсіңді,
   Бітіріпсің ісіңді.
   Атаңа лағынет, қарақшы,
   Құдайым сені қарғасын!
   Басыңа қиын іс түссе,
   Қасыңа досың бармасын!
   Сырлыбайдың алты ұлы,
   Алтауы бірдей бөрі еді.
   Отырған жылап Жібектің
   Тұсына жетіп келеді.
   Қыз Жібектің тұсында
   Бекежанды көреді.
   Көкжорға атты таниды,
   Бір сұмдықтың болғанын
   Сонда бұлар біледі.
   Бекежандай батырды
   Енді ортаға алады.
   Мойнына арқан салады.
   Сүйретіп барып алтауы
   Құрбандық қылып шалады..."
        </div>
        <div class="subtitle">Анықтамаларды терминдерге сәйкестендіріңіз</div>
        <div class="score-display">
            Дұрыс жауаптар: <span id="score">0</span> / <span id="total">6</span>
        </div>
        
        <div class="game-area">
            <div class="column terms-column" id="terms">
                <div class="term" data-id="1">кәззап</div>
                <div class="term" data-id="2">теріс бата</div>
                <div class="term" data-id="3">тез</div>
                <div class="term" data-id="4">тезге салу</div>
                <div class="term" data-id="5">қорамсақ</div>
                <div class="term" data-id="6">білте</div>
            </div>
            
            <div class="column definitions-column" id="definitions">
                <!-- Анықтамалар JavaScript арқылы толтырылады -->
            </div>
        </div>
        
        <div class="controls">
            <button id="check-btn">Жауаптарды тексеру</button>
            <button id="reset-btn">Қайта бастау</button>
            <button id="show-answers-btn" class="secondary">Дұрыс жауаптарды көрсету</button>
        </div>
        
        <div class="answer-key" id="answer-key">
            <h3>Дұрыс жауаптар:</h3>
            <div class="answer-item">
                <span class="answer-term">кәззап</span>
                <span class="answer-definition">жұғымсыз, қу</span>
            </div>
            <div class="answer-item">
                <span class="answer-term">теріс бата</span>
                <span class="answer-definition">қатты қарғыс, жазаның ауыр түрі</span>
            </div>
            <div class="answer-item">
                <span class="answer-term">тез</span>
                <span class="answer-definition">киіз үйдің жабдықтарын жасағанда ағаштың қисығын түзететін құрал</span>
            </div>
            <div class="answer-item">
                <span class="answer-term">тезге салу</span>
                <span class="answer-definition">теріс әрекет жасағанды күшпен жазалау</span>
            </div>
            <div class="answer-item">
                <span class="answer-term">қорамсақ</span>
                <span class="answer-definition">садақ оғы (жебе) қабының бір түрі</span>
            </div>
            <div class="answer-item">
                <span class="answer-term">білте</span>
                <span class="answer-definition">білтелі мылтыққа от алдыру үшін матадан ширатылып жасалады</span>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Жауаптардың дұрыс жұптары
            const correctMatches = {
                '1': 'B', // кәззап - жұғымсыз, қу
                '2': 'C', // теріс бата - қатты қарғыс
                '3': 'D', // тез - ағашты түзететін құрал
                '4': 'E', // тезге салу - күшпен жазалау
                '5': 'A', // қорамсақ - садақ оғы
                '6': 'F'  // білте - мылтыққа от алдыру
            };
            
            const definitions = {
                'A': 'садақ оғы (жебе) қабының бір түрі',
                'B': 'жұғымсыз, қу',
                'C': 'қатты қарғыс, жазаның ауыр түрі',
                'D': 'киіз үйдің жабдықтарын жасағанда ағаштың қисығын түзететін құрал',
                'E': 'теріс әрекет жасағанды күшпен жазалау',
                'F': 'білтелі мылтыққа от алдыру үшін матадан ширатылып жасалады'
            };
            
            let draggedItem = null;
            let matches = {};
            let score = 0;
            const totalItems = Object.keys(correctMatches).length;
            document.getElementById('total').textContent = totalItems;
            
            // Анықтамаларды кездейсоқ орналастыру
            function shuffleDefinitions() {
                const definitionsContainer = document.getElementById('definitions');
                definitionsContainer.innerHTML = '';
                
                // Анықтамаларды кездейсоқ реттеу
                const definitionIds = Object.keys(definitions);
                shuffleArray(definitionIds);
                
                // Анықтамаларды қосу
                definitionIds.forEach(id => {
                    const definition = document.createElement('div');
                    definition.className = 'definition';
                    definition.setAttribute('data-id', id);
                    definition.setAttribute('draggable', 'true');
                    definition.textContent = definitions[id];
                    
                    // Drag-and-drop функцияларын қосу
                    definition.addEventListener('dragstart', dragStart);
                    definition.addEventListener('dragover', dragOver);
                    definition.addEventListener('dragenter', dragEnter);
                    definition.addEventListener('dragleave', dragLeave);
                    definition.addEventListener('drop', drop);
                    definition.addEventListener('dragend', dragEnd);
                    
                    definitionsContainer.appendChild(definition);
                });
            }
            
            // Массивті кездейсоқ реттеу функциясы
            function shuffleArray(array) {
                for (let i = array.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [array[i], array[j]] = [array[j], array[i]];
                }
                return array;
            }
            
            // Бастапқы орнату
            shuffleDefinitions();
            
            // Drag-and-drop функциялары
            function dragStart(e) {
                draggedItem = this;
                setTimeout(() => {
                    this.classList.add('dragging');
                }, 0);
                e.dataTransfer.effectAllowed = 'move';
                e.dataTransfer.setData('text/html', this.innerHTML);
            }
            
            function dragOver(e) {
                e.preventDefault();
                return false;
            }
            
            function dragEnter(e) {
                e.preventDefault();
                if (this !== draggedItem) {
                    this.classList.add('over');
                }
            }
            
            function dragLeave() {
                this.classList.remove('over');
            }
            
            function drop(e) {
                e.stopPropagation();
                e.preventDefault();
                
                this.classList.remove('over');
                
                // Тек анықтамалардың орнын ауыстыру
                if (draggedItem.classList.contains('definition') && this.classList.contains('definition')) {
                    // Элементтердің мәтінін ауыстыру
                    const tempText = this.textContent;
                    const tempId = this.getAttribute('data-id');
                    
                    this.textContent = draggedItem.textContent;
                    this.setAttribute('data-id', draggedItem.getAttribute('data-id'));
                    
                    draggedItem.textContent = tempText;
                    draggedItem.setAttribute('data-id', tempId);
                }
                
                return false;
            }
            
            function dragEnd() {
                this.classList.remove('dragging');
                document.querySelectorAll('.definition').forEach(item => item.classList.remove('over'));
            }
            
            // Терминдер мен анықтамаларды сәйкестендіру
            function matchDefinitions() {
                const termElements = document.querySelectorAll('.term');
                const definitionElements = document.querySelectorAll('.definition');
                
                matches = {};
                
                termElements.forEach(term => {
                    const termId = term.getAttribute('data-id');
                    const termRect = term.getBoundingClientRect();
                    
                    // Әрбір терминге ең жақын анықтаманы табу
                    let closestDef = null;
                    let minDistance = Infinity;
                    
                    definitionElements.forEach(def => {
                        if (!def.classList.contains('matched')) {
                            const defRect = def.getBoundingClientRect();
                            const distance = Math.abs(termRect.top - defRect.top);
                            
                            if (distance < minDistance) {
                                minDistance = distance;
                                closestDef = def;
                            }
                        }
                    });
                    
                    if (closestDef) {
                        const defId = closestDef.getAttribute('data-id');
                        matches[termId] = defId;
                        closestDef.classList.add('matched');
                    }
                });
            }
            
            // Жауаптарды тексеру
            function checkAnswers() {
                matchDefinitions();
                
                let correctCount = 0;
                
                // Барлық жұптарды тексеру
                for (const termId in matches) {
                    const defId = matches[termId];
                    
                    if (correctMatches[termId] === defId) {
                        correctCount++;
                    }
                }
                
                // Ұпайды жаңарту
                score = correctCount;
                document.getElementById('score').textContent = score;
                
                // Дұрыс және қате жауаптарды белгілеу
                document.querySelectorAll('.definition').forEach(def => {
                    const defId = def.getAttribute('data-id');
                    let isCorrect = false;
                    
                    for (const termId in matches) {
                        if (matches[termId] === defId && correctMatches[termId] === defId) {
                            isCorrect = true;
                            break;
                        }
                    }
                    
                    if (isCorrect) {
                        def.classList.add('correct');
                    } else {
                        def.classList.add('incorrect');
                    }
                });
                
                // Түймені өшіру
                document.getElementById('check-btn').disabled = true;
            }
            
            // Ойынды қайта бастау
            function resetGame() {
                // Барлық жұптарды жою
                matches = {};
                score = 0;
                document.getElementById('score').textContent = score;
                
                // Анықтамаларды қайта орналастыру
                shuffleDefinitions();
                
                // Түймені қосу
                document.getElementById('check-btn').disabled = false;
                
                // Жауаптар кестесін жасыру
                document.getElementById('answer-key').style.display = 'none';
            }
            
            // Дұрыс жауаптарды көрсету
            function showAnswers() {
                document.getElementById('answer-key').style.display = 'block';
            }
            
            // Түймелерге функцияларды байлау
            document.getElementById('check-btn').addEventListener('click', checkAnswers);
            document.getElementById('reset-btn').addEventListener('click', resetGame);
            document.getElementById('show-answers-btn').addEventListener('click', showAnswers);
        });
    </script>
</body>
</html>  
