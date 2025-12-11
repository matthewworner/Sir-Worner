<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wally Worner and the Two Sieges of Malta</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #8b4513 0%, #d2691e 50%, #8b4513 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .book-container {
            width: 95vw;
            max-width: 1400px;
            height: 92vh;
            background: linear-gradient(to right, #f4e4c1 0%, #f9f3e6 2%, #fff8ed 50%, #f9f3e6 98%, #f4e4c1 100%);
            border-radius: 15px;
            box-shadow: 
                0 0 0 8px #8b4513,
                0 0 0 12px #d2691e,
                0 20px 60px rgba(0,0,0,0.5),
                inset 0 2px 10px rgba(139,69,19,0.1);
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        /* Book spine effect */
        .book-container::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 40px;
            background: linear-gradient(to right, 
                rgba(139,69,19,0.3) 0%,
                rgba(139,69,19,0.1) 50%,
                transparent 100%);
            pointer-events: none;
            z-index: 10;
        }

        .header {
            background: linear-gradient(135deg, #8b0000, #a52a2a);
            color: #ffd700;
            padding: 20px;
            text-align: center;
            border-bottom: 3px solid #8b4513;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }

        .header h1 {
            font-size: 32px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            margin-bottom: 5px;
        }

        .header p {
            font-size: 16px;
            font-style: italic;
            color: #ffe4b5;
        }

        .page {
            flex: 1;
            display: none;
            flex-direction: row;
            padding: 30px 50px;
            position: relative;
            animation: pageFlip 0.8s ease-in-out;
            background: 
                linear-gradient(90deg, transparent 0%, transparent 2%, #fff 2%, #fff 98%, transparent 98%, transparent 100%),
                repeating-linear-gradient(0deg, #f5e6d3 0px, #f5e6d3 1px, transparent 1px, transparent 30px);
        }

        .page.active {
            display: flex;
        }

        @keyframes pageFlip {
            0% {
                opacity: 0;
                transform: perspective(1000px) rotateY(-15deg);
            }
            100% {
                opacity: 1;
                transform: perspective(1000px) rotateY(0deg);
            }
        }

        .page-left {
            flex: 1;
            padding-right: 30px;
            border-right: 2px dashed #d2b48c;
            display: flex;
            flex-direction: column;
        }

        .page-right {
            flex: 1;
            padding-left: 30px;
            display: flex;
            flex-direction: column;
        }

        .illustration {
            width: 100%;
            height: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
            position: relative;
            border: 3px solid #8b4513;
            border-radius: 10px;
            background: #f5f5dc;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .illustration img {
            max-width: 100%;
            max-height: 100%;
            object-fit: cover;
            border-radius: 8px;
            transition: transform 0.3s ease;
        }

        .illustration img:hover {
            transform: scale(1.05);
        }

        .illustration-caption {
            position: absolute;
            bottom: 10px;
            left: 10px;
            right: 10px;
            background: rgba(139,69,19,0.9);
            color: #ffd700;
            padding: 8px;
            font-size: 12px;
            text-align: center;
            border-radius: 5px;
            font-style: italic;
        }

        .text-content {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            background: rgba(255,248,237,0.8);
            border: 2px solid #d2b48c;
            border-radius: 10px;
            font-size: 16px;
            line-height: 1.8;
            box-shadow: inset 0 2px 8px rgba(139,69,19,0.1);
        }

        .text-content::-webkit-scrollbar {
            width: 8px;
        }

        .text-content::-webkit-scrollbar-track {
            background: #f5e6d3;
            border-radius: 4px;
        }

        .text-content::-webkit-scrollbar-thumb {
            background: #8b4513;
            border-radius: 4px;
        }

        h2 {
            color: #8b0000;
            margin-bottom: 15px;
            font-size: 24px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
            border-bottom: 2px solid #d2691e;
            padding-bottom: 5px;
        }

        .text-content p {
            margin-bottom: 12px;
            text-align: justify;
        }

        .text-content em {
            color: #8b0000;
            font-style: italic;
        }

        .motto {
            text-align: center;
            font-style: italic;
            color: #8b0000;
            font-size: 18px;
            font-weight: bold;
            padding: 15px;
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            border: 3px solid #8b4513;
            border-radius: 10px;
            margin: 15px 0;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        .controls {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 20px;
            z-index: 100;
        }

        button {
            padding: 12px 30px;
            font-size: 18px;
            background: linear-gradient(135deg, #8b0000, #a52a2a);
            color: #ffd700;
            border: 3px solid #8b4513;
            border-radius: 25px;
            cursor: pointer;
            font-family: 'Georgia', serif;
            font-weight: bold;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        button:hover:not(:disabled) {
            background: linear-gradient(135deg, #a52a2a, #cd5c5c);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.4);
        }

        button:disabled {
            background: #999;
            cursor: not-allowed;
            opacity: 0.5;
        }

        .page-number {
            position: absolute;
            bottom: 10px;
            font-size: 14px;
            color: #8b4513;
            font-style: italic;
        }

        .page-left .page-number {
            left: 40px;
        }

        .page-right .page-number {
            right: 40px;
        }

        .book-selector {
            position: absolute;
            top: 20px;
            right: 20px;
            z-index: 50;
        }

        .book-selector select {
            padding: 10px 20px;
            font-size: 16px;
            background: #ffd700;
            border: 2px solid #8b4513;
            border-radius: 20px;
            font-family: 'Georgia', serif;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 3px 10px rgba(0,0,0,0.3);
        }

        /* Animated elements */
        .clickable {
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .clickable:hover {
            transform: scale(1.1);
        }

        .sound-toggle {
            position: absolute;
            top: 20px;
            left: 20px;
            z-index: 50;
            padding: 10px 20px;
            background: #ffd700;
            border: 2px solid #8b4513;
            border-radius: 20px;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 3px 10px rgba(0,0,0,0.3);
        }

        .rabbit-counter {
            position: absolute;
            top: 70px;
            left: 20px;
            z-index: 50;
            padding: 10px 15px;
            background: rgba(255,215,0,0.9);
            border: 2px solid #8b4513;
            border-radius: 15px;
            font-size: 14px;
            font-weight: bold;
            color: #8b0000;
            box-shadow: 0 3px 10px rgba(0,0,0,0.3);
        }

        .hidden-rabbit {
            position: absolute;
            font-size: 20px;
            cursor: pointer;
            transition: transform 0.3s ease;
            animation: hop 2s ease-in-out infinite;
        }

        .hidden-rabbit:hover {
            transform: scale(1.3);
        }

        .hidden-rabbit.found {
            opacity: 0.5;
        }

        @keyframes hop {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        /* Special effects for Stella photos */
        .stella-glow {
            box-shadow: 0 0 20px #ffd700, 0 0 40px #ffed4e;
            animation: stellaShine 3s ease-in-out infinite;
        }

        @keyframes stellaShine {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.2); }
        }

        .interactive-map {
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, #87ceeb 0%, #4682b4 100%);
            position: relative;
            border-radius: 10px;
            overflow: hidden;
        }

        .map-location {
            position: absolute;
            width: 20px;
            height: 20px;
            background: #ff0000;
            border-radius: 50%;
            border: 3px solid #fff;
            cursor: pointer;
            transition: transform 0.3s ease;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        .map-location:hover {
            transform: scale(1.5);
        }
    </style>
</head>
<body>
    <div class="book-container">
        <div class="header">
            <h1>The Wally Worner Chronicles</h1>
            <p>Two Heroes • Two Sieges • One House • 375 Years Apart</p>
        </div>

        <div class="sound-toggle" onclick="toggleSound()">🔊 Sound: ON</div>
        <div class="rabbit-counter">🐰 Rabbits Found: <span id="rabbitCount">0</span>/16</div>
        
        <div class="book-selector">
            <select onchange="changeBook(this.value)">
                <option value="book1">Book 1: The Great Siege (1565)</option>
                <option value="book2">Book 2: Fortress Malta (WWII)</option>
            </select>
        </div>

        <!-- BOOK 1: THE GREAT SIEGE (1565) -->
        <div class="page active book1-page" data-page="1">
            <div class="page-left">
                <div class="illustration stella-glow">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect fill='%23f5e6d3' width='400' height='300'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' fill='%238b4513' font-size='20' font-family='serif'%3EWorner Coat of Arms%3C/text%3E%3C/svg%3E" alt="Worner Coat of Arms">
                    <div class="illustration-caption">The Worner Family Coat of Arms - Yellow shield, red stripe, six red roses</div>
                </div>
                <div class="text-content">
                    <h2>The Wally Worner Chronicles</h2>
                    <div class="motto">Non nobis tantum nati<br>"Not born for ourselves alone"</div>
                    <p><strong>Book One: The Great Siege of Malta, 1565</strong></p>
                    <p>Long ago, there lived a brave knight named <strong>Sir Wallace "Wally" Worner</strong>. His name meant "guardian warrior," and he carried a proud coat of arms—a bright yellow shield with a bold red diagonal stripe and six red roses.</p>
                    <p>Above his shield sat an armored arm, symbol of his strength. Flowing mantling in red and yellow surrounded it. And at the top, his family motto: <em>"Non nobis tantum nati"</em> — We are not born for ourselves alone.</p>
                    <p>This is the story of how Wally Worner became a Knight of St. John, fought alongside the legendary Jean de la Valette, and defended a house that would shine like a star through the centuries...</p>
                </div>
            </div>
            <div class="page-right">
                <div class="illustration">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect fill='%23667eea' width='400' height='300'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' fill='white' font-size='20' font-family='serif'%3EKnight of Malta%3C/text%3E%3C/svg%3E" alt="Wally Worner Knight">
                    <div class="illustration-caption">Sir Wallace "Wally" Worner - Knight of St. John with the Maltese Cross</div>
                </div>
                <div class="text-content">
                    <h2>Meet Wally Worner</h2>
                    <p>Wally wasn't the biggest knight or the strongest knight, but he was clever, brave, and kind. He always remembered his family's motto.</p>
                    <p>When he wasn't training with his sword or riding his horse, he loved helping people in his village. He'd fix roofs, carry water for the elderly, and tell stories to children.</p>
                    <p>"Why do you help everyone?" asked his young squire, Thomas.</p>
                    <p><em>"Because that's what our motto means,"</em> Wally replied, pointing to his yellow and red shield. <em>"We're not born just for ourselves. We're here to protect and help others. That's what makes a true knight."</em></p>
                    <p>Little did Wally know that soon he would have the chance to prove those words in the greatest test of his life...</p>
                </div>
            </div>
            <div class="hidden-rabbit" style="bottom: 50px; right: 100px;" onclick="findRabbit(this)">🐰</div>
            <div class="page-number">Page 1-2</div>
        </div>

        <!-- Page 2: The Call to Malta -->
        <div class="page book1-page" data-page="2">
            <div class="page-left">
                <div class="illustration">
                    <div class="interactive-map">
                        <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 24px; color: white; text-shadow: 2px 2px 4px black;">
                            Mediterranean Sea<br>
                            <span style="font-size: 16px;">Malta ⭐ | Ottoman Fleet ⚓</span>
                        </div>
                        <div class="map-location" style="top: 60%; left: 50%;" title="Malta - Grand Harbour"></div>
                    </div>
                    <div class="illustration-caption">The Mediterranean Sea - Malta's strategic position</div>
                </div>
                <div class="text-content">
                    <h2>The Call to Malta</h2>
                    <p>One spring morning in 1565, a messenger arrived at Wally's castle. He was covered in dust from riding hard for days.</p>
                    <p>"Sir Wally," the messenger gasped, "Malta is in terrible danger! The Ottoman Empire has sent hundreds of ships and thousands of soldiers to capture the island. Grand Master Jean de la Valette calls for all brave knights to come defend it!"</p>
                    <p>Wally knew about Malta. It was a small island in the Mediterranean Sea, home to the Knights of St. John—warriors who protected pilgrims and helped the sick. If Malta fell, the whole of Europe would be in danger.</p>
                    <p>He looked at his coat of arms hanging on the wall, then at young Thomas.</p>
                    <p><em>"Others need protection, and that is what a Worner does. Pack my armor, Thomas. We sail for Malta!"</em></p>
                </div>
            </div>
            <div class="page-right">
                <div class="illustration">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect fill='%234682b4' width='400' height='300'/%3E%3Cpath d='M50,250 Q100,200 150,250 Q200,200 250,250 Q300,200 350,250' stroke='white' stroke-width='3' fill='none' opacity='0.6'/%3E%3Ctext x='50%25' y='40%25' text-anchor='middle' fill='white' font-size='20' font-family='serif'%3E⛵ The Voyage%3C/text%3E%3C/svg%3E" alt="Ship">
                    <div class="illustration-caption">Sailing across the stormy Mediterranean</div>
                </div>
                <div class="text-content">
                    <h2>The Perilous Voyage</h2>
                    <p>The voyage was Wally's first great adventure. The Mediterranean could be beautiful, but it could also be deadly. Storms rose without warning. Pirates lurked near every coast—Turkish corsairs and Barbary raiders who showed no mercy.</p>
                    <p>One night, a terrible storm hit. Lightning cracked across the sky. Waves taller than castles crashed over the ship's deck. The sailors cried out in fear.</p>
                    <p>But Wally noticed something strange. Through breaks in the clouds, he saw stars arranged in a pattern he'd never seen before—almost like they were pointing a way.</p>
                    <p><em>"Captain!"</em> Wally shouted over the wind. <em>"Follow those stars! Change course to the east!"</em></p>
                    <p>The captain trusted him. By morning, they sailed into calm waters. And there, golden in the sunrise, stood Malta—the island fortress that would become Wally's destiny.</p>
                </div>
            </div>
            <div class="hidden-rabbit" style="top: 150px; left: 80px;" onclick="findRabbit(this)">🐰</div>
            <div class="page-number">Page 3-4</div>
        </div>

        <!-- Page 3: Stella House -->
        <div class="page book1-page" data-page="3">
            <div class="page-left">
                <div class="illustration stella-glow">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect fill='%23f4a460' width='400' height='300'/%3E%3Ctext x='50%25' y='30%25' text-anchor='middle' fill='%238b4513' font-size='24' font-family='serif'%3E38 Triq il-Kurcifiss%3C/text%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' fill='gold' font-size='40'%3E⭐%3C/text%3E%3Ctext x='50%25' y='70%25' text-anchor='middle' fill='%238b4513' font-size='20' font-family='serif'%3ESTELLA%3C/text%3E%3C/svg%3E" alt="Stella House">
                    <div class="illustration-caption">✨ THIS IS THE REAL STELLA - Your family's house in Senglea! ✨</div>
                </div>
                <div class="text-content">
                    <h2>Discovering Stella</h2>
                    <p>Wally met Jean de la Valette, the Grand Master of the Knights—a legendary warrior with steel-gray eyes. Valette looked at Wally's coat of arms and nodded approvingly.</p>
                    <p><em>"'Not born for ourselves alone.' Good. We need men who believe that. The Ottomans will attack Senglea first. If Senglea falls, Malta falls."</em></p>
                    <p>That night, Wally explored Senglea. He walked down <strong>Triq il-Kurcifiss</strong>—the Street of the Crucifix. The houses were built of beautiful golden limestone, their walls thick and strong.</p>
                    <p>One house caught his eye: <strong>number 38</strong>. It stood proudly, with windows overlooking the harbor. An old Maltese woman saw him looking.</p>
                    <p><em>"Fine house, no?"</em> she said in accented English. <em>"My family has lived here for generations. Protect us, Sir Knight."</em></p>
                    <p>She handed him fresh bread and cheese. Wally looked at the house, at the woman's hopeful face, and made a promise:</p>
                    <p><em>"I will. This house will stand."</em></p>
                </div>
            </div>
            <div class="page-right">
                <div class="illustration">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect fill='%23d2b48c' width='400' height='300'/%3E%3Crect fill='%23ffd700' x='150' y='100' width='100' height='120' stroke='%238b0000' stroke-width='3'/%3E%3Cpath d='M150,100 L200,50 L250,100' fill='%238b0000'/%3E%3Ctext x='50%25' y='90%25' text-anchor='middle' fill='%238b0000' font-size='18' font-family='serif'%3ESenglea Fortress%3C/text%3E%3C/svg%3E" alt="Senglea">
                    <div class="illustration-caption">Senglea - The peninsula fortress that guards Grand Harbour</div>
                </div>
                <div class="text-content">
                    <h2>The Importance of Senglea</h2>
                    <p>Senglea was a narrow peninsula jutting into Grand Harbour, surrounded by water on three sides. Its position made it incredibly important—and incredibly vulnerable.</p>
                    <p>Jean de la Valette explained the strategy: <em>"Senglea, Birgu, and Fort St. Angelo form a triangle of defense. If one falls, the others are doomed. We must hold all three."</em></p>
                    <p>But there were only about 6,000 defenders—knights, soldiers, and brave Maltese citizens. The Ottoman force had over 40,000 men.</p>
                    <p>Wally walked the walls of Senglea that night. He could see the massive Ottoman camp across the harbor, their campfires like stars on the ground. Tomorrow, the siege would begin.</p>
                    <p>He thought about the house at number 38, about the old woman and her family, about all the people depending on him.</p>
                    <p><em>"Non nobis tantum nati,"</em> he whispered to the stars. <em>"Not for ourselves alone."</em></p>
                    <p>He would not let them down.</p>
                </div>
            </div>
            <div class="hidden-rabbit" style="bottom: 100px; right: 150px;" onclick="findRabbit(this)">🐰</div>
            <div class="page-number">Page 5-6</div>
        </div>

        <!-- Continue with more pages... -->
        
        <div class="controls">
            <button id="prevBtn" onclick="previousPage()">← Previous</button>
            <button id="nextBtn" onclick="nextPage()">Next →</button>
        </div>
    </div>

    <script>
        let currentPage = 0;
        let currentBook = 'book1';
        let soundEnabled = true;
        let rabbitsFound = 0;
        const totalRabbits = 16; // 8 per book

        function showPage(index) {
            const pages = document.querySelectorAll(`.${currentBook}-page`);
            pages.forEach((page, i) => {
                page.classList.remove('active');
                if (i === index) {
                    page.classList.add('active');
                    if (soundEnabled) playPageTurnSound();
                }
            });

            document.getElementById('prevBtn').disabled = index === 0;
            document.getElementById('nextBtn').disabled = index === pages.length - 1;
        }

        function nextPage() {
            const pages = document.querySelectorAll(`.${currentBook}-page`);
            if (currentPage < pages.length - 1) {
                currentPage++;
                showPage(currentPage);
            }
        }

        function previousPage() {
            if (currentPage > 0) {
                currentPage--;
                showPage(currentPage);
            }
        }

        function changeBook(book) {
            currentBook = book;
            currentPage = 0;
            showPage(0);
        }

        function toggleSound() {
            soundEnabled = !soundEnabled;
            document.querySelector('.sound-toggle').textContent = soundEnabled ? '🔊 Sound: ON' : '🔇 Sound: OFF';
        }

        function playPageTurnSound() {
            // Placeholder for sound effect
            console.log('Page turn sound');
        }

        function findRabbit(element) {
            if (!element.classList.contains('found')) {
                element.classList.add('found');
                rabbitsFound++;
                document.getElementById('rabbitCount').textContent = rabbitsFound;
                
                if (rabbitsFound === totalRabbits) {
                    alert('🎉 Congratulations! You found all the rabbits! You\'re a true Malta explorer! 🐰⭐');
                }
            }
        }

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight') nextPage();
            if (e.key === 'ArrowLeft') previousPage();
        });

        showPage(0);
    </script>
</body>
</html>