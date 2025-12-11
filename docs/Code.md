<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sir Worner and the Siege of Senglea</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .book-container {
            width: 90vw;
            max-width: 1200px;
            height: 90vh;
            background: #f5e6d3;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.4);
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        .page {
            flex: 1;
            display: none;
            flex-direction: column;
            padding: 40px;
            position: relative;
            animation: pageFlip 0.6s ease-in-out;
        }

        .page.active {
            display: flex;
        }

        @keyframes pageFlip {
            from {
                opacity: 0;
                transform: rotateY(-20deg);
            }
            to {
                opacity: 1;
                transform: rotateY(0);
            }
        }

        .illustration {
            width: 100%;
            height: 55%;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            margin-bottom: 20px;
        }

        .illustration img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            filter: drop-shadow(0 10px 10px rgba(0,0,0,0.2));
        }

        .text-content {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            background: rgba(255,255,255,0.7);
            border-radius: 10px;
            font-size: 18px;
            line-height: 1.6;
        }

        h1 {
            color: #8b0000;
            margin-bottom: 15px;
            text-align: center;
            font-size: 28px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .controls {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 20px;
            z-index: 100;
        }

        button {
            padding: 12px 30px;
            font-size: 18px;
            background: #8b0000;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-family: inherit;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        button:hover {
            background: #a52a2a;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.4);
        }

        button:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        /* Animation classes for images */
        .anim-float {
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
        }

        .anim-sail {
            animation: sail 4s ease-in-out infinite;
        }

        @keyframes sail {
            0%, 100% { transform: rotate(-2deg); }
            50% { transform: rotate(2deg); }
        }

        .anim-glow {
            animation: glow 3s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { filter: drop-shadow(0 0 10px gold) brightness(1); }
            50% { filter: drop-shadow(0 0 20px gold) brightness(1.1); }
        }

        .anim-battle {
            animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) infinite;
        }

        @keyframes shake {
            10%, 90% { transform: translate3d(-1px, 0, 0); }
            20%, 80% { transform: translate3d(2px, 0, 0); }
            30%, 50%, 70% { transform: translate3d(-2px, 0, 0); }
            40%, 60% { transform: translate3d(2px, 0, 0); }
        }

        .star-overlay {
            position: absolute;
            top: 20%;
            left: 50%;
            transform: translateX(-50%);
            width: 50px;
            animation: twinkle 2s ease-in-out infinite;
            z-index: 10;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 1; transform: translateX(-50%) scale(1); }
            50% { opacity: 0.5; transform: translateX(-50%) scale(1.3); }
        }

        .page-number {
            position: absolute;
            bottom: 10px;
            right: 20px;
            font-size: 14px;
            color: #666;
        }
        
        .illustration-group {
            position: relative;
            height: 100%;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
</head>
<body>
    <div class="book-container">
        <!-- Page 1: Title -->
        <div class="page active">
            <div class="illustration">
                <img src="worner.png" alt="Sir Worner" class="anim-float">
            </div>
            <div class="text-content">
                <h1>Sir Worner and the Siege of Senglea</h1>
                <p><strong>A Tale of Courage and Honor</strong></p>
                <p style="margin-top: 20px;">Long ago in 1565, there lived a brave knight named Sir Worner. His name meant "guardian warrior," and he carried a bright yellow shield with a bold red stripe and six red flowers.</p>
                <p style="margin-top: 15px;">His family motto was: <em>"Non nobis tantum nati"</em> — "Not born for ourselves alone."</p>
                <p style="margin-top: 15px;">This is the story of how Sir Worner helped save Malta and defended a special house that would shine like a star through the centuries...</p>
            </div>
            <div class="page-number">Page 1</div>
        </div>

        <!-- Page 2: The Call -->
        <div class="page">
            <div class="illustration">
                <img src="castle.png" alt="Castle" class="anim-float">
            </div>
            <div class="text-content">
                <h1>The Call to Malta</h1>
                <p>One spring morning, a messenger arrived at Sir Worner's castle with urgent news. The beautiful island of Malta was in terrible danger!</p>
                <p style="margin-top: 15px;">The Ottoman Empire had sent hundreds of ships carrying thousands of soldiers to capture the island. Malta was defended by the Knights of St. John, led by the great Grand Master Jean de la Valette, but they were outnumbered ten to one.</p>
                <p style="margin-top: 15px;">Sir Worner looked at his coat of arms. He thought about his motto. Then he made his decision.</p>
                <p style="margin-top: 15px;"><em>"I must go," he told his squire Thomas. "Others need protection, and that is what a Worner does."</em></p>
            </div>
            <div class="page-number">Page 2</div>
        </div>

        <!-- Page 3: The Voyage -->
        <div class="page">
            <div class="illustration">
                <img src="ship.png" alt="Ship" class="anim-sail">
            </div>
            <div class="text-content">
                <h1>The Journey Across the Sea</h1>
                <p>The voyage across the Mediterranean Sea was Sir Worner's first great adventure. His ship battled terrible storms. Lightning cracked the sky, and waves as tall as castles crashed over the deck.</p>
                <p style="margin-top: 15px;">One night, when all seemed lost, Sir Worner noticed something strange—the stars were arranged in a pattern he'd never seen before. Following his instincts, he convinced the captain to change course.</p>
                <p style="margin-top: 15px;">The next morning, they sailed into calm waters and spotted Malta on the horizon.</p>
                <p style="margin-top: 15px;"><em>"How did you know?"</em> asked Thomas, amazed.</p>
                <p style="margin-top: 15px;"><em>"Sometimes, a guardian must trust his heart as much as his sword,"</em> Sir Worner replied with a smile.</p>
            </div>
            <div class="page-number">Page 3</div>
        </div>

        <!-- Page 4: Meeting Valette -->
        <div class="page">
            <div class="illustration">
                <img src="fortress.png" alt="Fortress">
            </div>
            <div class="text-content">
                <h1>Meeting Jean de la Valette</h1>
                <p>When Sir Worner arrived at Malta, the island was already under siege. He was brought before Jean de la Valette himself—a legendary warrior with steel-gray hair and eyes that had seen a thousand battles.</p>
                <p style="margin-top: 15px;"><em>"Sir Worner, your motto—'Not born for ourselves alone.' We shall need men who believe such words. The Ottoman forces will strike at Senglea, the peninsula fortress. It is the key to our harbor. If Senglea falls, Malta falls."</em></p>
                <p style="margin-top: 15px;"><em>"Then Senglea must not fall,"</em> Sir Worner said firmly.</p>
                <p style="margin-top: 15px;">Jean de la Valette smiled for the first time in weeks. <em>"You will fight alongside me. Come, let me show you the fortress that will be your home—and perhaps your glory."</em></p>
            </div>
            <div class="page-number">Page 4</div>
        </div>

        <!-- Page 5: Senglea -->
        <div class="page">
            <div class="illustration">
                <img src="house_stella.png" alt="Stella House" class="anim-glow">
            </div>
            <div class="text-content">
                <h1>The House Called Stella</h1>
                <p>That night, Sir Worner explored the streets of Senglea. He walked down Triq il-Kurcifiss—the Street of the Crucifix. One house in particular caught his eye: number 38. It was strong, built of golden limestone, with a perfect view of the harbor.</p>
                <p style="margin-top: 15px;">An old woman gave him bread. <em>"Protect us, Sir Knight. This house has been in my family for generations."</em></p>
                <p style="margin-top: 15px;"><em>"I will,"</em> Sir Worner promised. <em>"This place will stand."</em></p>
                <p style="margin-top: 15px;">Little did he know that this house would become legendary—a shining star in Malta's darkest hour.</p>
            </div>
            <div class="page-number">Page 5</div>
        </div>

        <!-- Page 6: The Battle -->
        <div class="page">
            <div class="illustration">
                <img src="battle.png" alt="Battle" class="anim-battle">
            </div>
            <div class="text-content">
                <h1>The Great Battle for Senglea</h1>
                <p>On August 7th, 1565, the Ottomans launched their greatest assault. They attacked from both land and sea! Thousands of soldiers charged while boats filled with warriors approached from the harbor.</p>
                <p style="margin-top: 15px;">Jean de la Valette turned to Sir Worner: <em>"Take command of the harbor defenses. I trust you."</em></p>
                <p style="margin-top: 15px;">Sir Worner had a brilliant idea. He positioned cannons in the houses along Triq il-Kurcifiss, especially number 38. From its windows, they could see the entire harbor approach!</p>
                <p style="margin-top: 15px;">The house became a fortress within a fortress. Its thick walls absorbed enemy fire. Sir Worner fought from room to room, window to window, directing his men with precision.</p>
                <p style="margin-top: 15px;">All day the battle raged. By sunset, the Ottoman forces retreated. Senglea still stood, and number 38 had been the key to the harbor's defense!</p>
            </div>
            <div class="page-number">Page 6</div>
        </div>

        <!-- Page 7: The Gift -->
        <div class="page">
            <div class="illustration">
                <div class="illustration-group">
                    <img src="house_stella.png" alt="Stella House" class="anim-glow">
                    <img src="star.png" alt="Star" class="star-overlay">
                </div>
            </div>
            <div class="text-content">
                <h1>Stella - The Star</h1>
                <p>That evening, Jean de la Valette found Sir Worner outside number 38.</p>
                <p style="margin-top: 15px;"><em>"Today you saved Senglea. Your command from that house turned the tide of battle."</em></p>
                <p style="margin-top: 15px;">The Grand Master looked up at the house, still smoking from battle but standing proud and strong.</p>
                <p style="margin-top: 15px;"><em>"This house needs a name. It stood like a star of hope in our darkest hour. Let us call it 'Stella'—the Star."</em></p>
                <p style="margin-top: 15px;">Then Valette removed a ring from his finger—a band with the cross of the Knights of St. John.</p>
                <p style="margin-top: 15px;"><em>"I want you to have Stella—number 38 Triq il-Kurcifiss. It is yours, for you and your family, for all generations to come."</em></p>
                <p style="margin-top: 15px;">Sir Worner accepted with tears in his eyes. <em>"The Star. I will ensure it shines for generations."</em></p>
            </div>
            <div class="page-number">Page 7</div>
        </div>

        <!-- Page 8: The Legacy -->
        <div class="page">
            <div class="illustration">
                <div class="illustration-group" style="gap: 20px;">
                    <img src="worner.png" alt="Sir Worner" style="width: 40%;" class="anim-float">
                    <img src="house_stella.png" alt="Stella House" style="width: 60%;">
                </div>
            </div>
            <div class="text-content">
                <h1>The Legacy Lives On</h1>
                <p>The siege continued, but the great assault on Senglea was the turning point. The Ottoman forces eventually sailed away. Malta was saved!</p>
                <p style="margin-top: 15px;">Sir Worner made Stella his home. He restored its battle-damaged walls, planted flowers in its windows, and filled it with warmth and laughter. The house became a gathering place where Jean de la Valette was a frequent guest.</p>
                <p style="margin-top: 15px;">Years passed, then decades, then centuries. Stella remained, passed down through generations. Each generation added their stories, but never forgot the brave knight who defended it during the Great Siege.</p>
                <p style="margin-top: 15px;">People walking down Triq il-Kurcifiss would pause at number 38. "Stella," they would say. "The Star that helped save Malta."</p>
                <p style="margin-top: 15px;">And today, Stella still stands—a reminder that we are <em>Non nobis tantum nati</em>—not born for ourselves alone.</p>
            </div>
            <div class="page-number">Page 8</div>
        </div>

        <div class="controls">
            <button id="prevBtn" onclick="previousPage()">← Previous</button>
            <button id="nextBtn" onclick="nextPage()">Next →</button>
        </div>
    </div>

    <script>
        let currentPage = 0;
        const pages = document.querySelectorAll('.page');
        const prevBtn = document.getElementById('prevBtn');
        const nextBtn = document.getElementById('nextBtn');

        function showPage(index) {
            pages.forEach((page, i) => {
                page.classList.remove('active');
                if (i === index) {
                    page.classList.add('active');
                }
            });

            prevBtn.disabled = index === 0;
            nextBtn.disabled = index === pages.length - 1;
        }

        function nextPage() {
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

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight') nextPage();
            if (e.key === 'ArrowLeft') previousPage();
        });

        showPage(0);
    </script>
</body>
</html>