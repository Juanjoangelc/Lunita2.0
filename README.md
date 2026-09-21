<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Lunita 💛</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            overflow: hidden; /* Prevent scrolling */
            margin: 0;
            height: 100vh;
            width: 100vw;
            background-color: #fdfbfb;
        }

        .font-cursive {
            font-family: 'Dancing Script', cursive;
        }

        /* Full screen containers */
        .screen {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: absolute;
            top: 0;
            left: 0;
        }

        /* Transitions */
        .fade-out {
            animation: fadeOut 0.6s ease-in-out forwards;
        }

        .fade-in {
            animation: fadeIn 1s ease-in-out forwards;
            display: flex !important; /* Override hidden */
        }

        @keyframes fadeOut {
            from { opacity: 1; transform: scale(1); }
            to { opacity: 0; transform: scale(1.05); visibility: hidden; }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        /* Gift Box Animations */
        .gift-wrapper {
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .gift-wrapper:hover {
            transform: scale(1.05) translateY(-5px);
        }

        .gift-lid {
            transform-origin: bottom center;
            transition: transform 0.5s ease-in-out;
        }

        .opening .gift-lid {
            transform: translateY(-30px) rotate(10deg);
            opacity: 0;
        }

        .opening {
            animation: shakeGift 0.5s ease-in-out;
        }

        @keyframes shakeGift {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(-5deg); }
            50% { transform: rotate(5deg); }
            75% { transform: rotate(-5deg); }
        }

        /* Pulse Button */
        .pulse-btn {
            box-shadow: 0 0 0 0 rgba(236, 72, 153, 0.7);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(236, 72, 153, 0); }
            100% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0); }
        }

        /* Flowers and Petals */
        .flower-svg {
            position: absolute;
            opacity: 0;
            transform: scale(0) rotate(-20deg);
            transition: all 1.2s cubic-bezier(0.34, 1.56, 0.64, 1);
            z-index: 1;
        }

        .flower-svg.bloom {
            opacity: 1;
            transform: scale(1) rotate(0deg);
        }

        .floating {
            animation: float 4s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
        }

        .petal {
            position: absolute;
            top: -10%;
            background-color: #FBBF24;
            border-radius: 50% 0 50% 0;
            opacity: 0.8;
            pointer-events: none;
            z-index: 5;
            animation: fall linear infinite;
        }

        @keyframes fall {
            0% { transform: translateY(-5vh) rotate(0deg) scale(0.6); opacity: 0; }
            10% { opacity: 1; }
            100% { transform: translateY(105vh) rotate(360deg) scale(1.2); opacity: 0; }
        }

        .message-box {
            z-index: 10;
            opacity: 0;
            transform: translateY(30px);
            transition: all 1s ease-out 0.8s; /* Delayed appearance */
        }

        .fade-in .message-box {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>

    <!-- Screen 1: Gift Screen -->
    <div id="screen-1" class="screen bg-gradient-to-br from-pink-100 to-rose-200 z-20">
        <h1 class="text-4xl md:text-5xl font-cursive text-pink-600 mb-10 drop-shadow-sm text-center px-4 font-bold">
            Un detalle para ti, Lunita 🌙
        </h1>
        
        <div class="gift-wrapper" id="gift-element">
            <svg width="220" height="220" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg" class="drop-shadow-2xl">
                <!-- Box -->
                <rect x="35" y="85" width="130" height="95" rx="6" fill="#F472B6"/>
                <!-- Ribbon vertical -->
                <rect x="85" y="85" width="30" height="95" fill="#FDE047"/>
                
                <!-- Lid -->
                <g class="gift-lid">
                    <rect x="25" y="60" width="150" height="25" rx="4" fill="#EC4899"/>
                    <rect x="85" y="60" width="30" height="25" fill="#FACC15"/>
                    <!-- Bow -->
                    <path d="M100 60 C 50 0, 10 30, 90 60" fill="#FDE047" stroke="#EAB308" stroke-width="2"/>
                    <path d="M100 60 C 150 0, 190 30, 110 60" fill="#FDE047" stroke="#EAB308" stroke-width="2"/>
                    <circle cx="100" cy="60" r="10" fill="#EAB308"/>
                </g>
            </svg>
        </div>

        <button id="btn-open" class="mt-12 bg-pink-500 hover:bg-pink-600 text-white font-bold py-3 px-8 rounded-full text-lg transition-colors pulse-btn flex items-center gap-2 shadow-lg">
            <span>Abrir Regalo</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 11l7-7 7 7M5 19l7-7 7 7" />
            </svg>
        </button>
    </div>

    <!-- Screen 2: Surprise Screen (Hidden by default) -->
    <div id="screen-2" class="screen bg-gradient-to-br from-yellow-50 to-orange-100 hidden z-10">
        
        <!-- Decorative Flowers -->
        <!-- Top Left -->
        <div class="flower-svg floating" style="top: 8%; left: 5%; width: 130px; animation-delay: 0s;">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="drop-shadow-lg">
                <!-- Petals -->
                <g fill="#FDE047" stroke="#EAB308" stroke-width="1">
                    <circle cx="50" cy="20" r="18"/><circle cx="50" cy="80" r="18"/>
                    <circle cx="20" cy="50" r="18"/><circle cx="80" cy="50" r="18"/>
                    <circle cx="28" cy="28" r="18"/><circle cx="72" cy="72" r="18"/>
                    <circle cx="28" cy="72" r="18"/><circle cx="72" cy="28" r="18"/>
                </g>
                <!-- Center -->
                <circle cx="50" cy="50" r="15" fill="#A16207"/>
                <circle cx="50" cy="50" r="10" fill="#713F12" opacity="0.5"/>
            </svg>
        </div>

        <!-- Bottom Right -->
        <div class="flower-svg floating" style="bottom: 10%; right: 5%; width: 160px; animation-delay: 0.5s;">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="drop-shadow-lg">
                <g fill="#FACC15" stroke="#CA8A04" stroke-width="1">
                    <ellipse cx="50" cy="20" rx="15" ry="25"/><ellipse cx="50" cy="80" rx="15" ry="25"/>
                    <ellipse cx="20" cy="50" rx="25" ry="15"/><ellipse cx="80" cy="50" rx="25" ry="15"/>
                    <ellipse cx="30" cy="30" rx="20" ry="20"/><ellipse cx="70" cy="70" rx="20" ry="20"/>
                    <ellipse cx="30" cy="70" rx="20" ry="20"/><ellipse cx="70" cy="30" rx="20" ry="20"/>
                </g>
                <circle cx="50" cy="50" r="16" fill="#854D0E"/>
            </svg>
        </div>

        <!-- Top Right -->
        <div class="flower-svg floating" style="top: 15%; right: 10%; width: 100px; animation-delay: 1s;">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="drop-shadow-md">
                <g fill="#FEF08A">
                    <circle cx="50" cy="25" r="15"/><circle cx="50" cy="75" r="15"/>
                    <circle cx="25" cy="50" r="15"/><circle cx="75" cy="50" r="15"/>
                    <circle cx="32" cy="32" r="15"/><circle cx="68" cy="68" r="15"/>
                    <circle cx="32" cy="68" r="15"/><circle cx="68" cy="32" r="15"/>
                </g>
                <circle cx="50" cy="50" r="12" fill="#CA8A04"/>
            </svg>
        </div>

        <!-- Bottom Left -->
        <div class="flower-svg floating" style="bottom: 15%; left: 8%; width: 120px; animation-delay: 1.5s;">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" class="drop-shadow-md">
                <g fill="#FDE047">
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(0 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(45 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(90 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(135 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(180 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(225 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(270 50 50)"/>
                    <path d="M50 40 C 30 10, 70 10, 50 40" transform="rotate(315 50 50)"/>
                </g>
                <circle cx="50" cy="50" r="14" fill="#B45309"/>
            </svg>
        </div>

        <!-- Message Card -->
        <div class="message-box bg-white/80 backdrop-blur-sm p-8 md:p-12 rounded-3xl shadow-2xl border-2 border-yellow-300 w-11/12 max-w-lg text-center mx-4">
            <h2 class="font-cursive text-5xl md:text-6xl text-yellow-600 mb-6 drop-shadow-sm leading-tight">
                ¡Sorpresa,<br> mi Lunita! 🌻
            </h2>
            
            <p class="text-gray-700 text-lg md:text-xl font-medium mb-4">
                Dicen que hoy es el día de regalar flores amarillas a esas personas que iluminan nuestra vida con su presencia.
            </p>
            <p class="text-gray-700 text-lg md:text-xl font-medium mb-6">
                Tú eres exactamente eso. Que el color y la luz de estas flores te recuerden siempre lo especial, brillante y maravillosa que eres (se que no te gusta el amarillo pero es bonito igual el detalle supongo).
            </p>
            
            <div class="text-3xl animate-bounce mt-4">
                💛 🌙 ✨
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const btnOpen = document.getElementById('btn-open');
            const giftElement = document.getElementById('gift-element');
            const screen1 = document.getElementById('screen-1');
            const screen2 = document.getElementById('screen-2');
            const flowers = document.querySelectorAll('.flower-svg');
            
            let isOpened = false;

            function openGift() {
                if (isOpened) return;
                isOpened = true;

                // 1. Play opening animation on the gift
                giftElement.classList.add('opening');

                // 2. After a short delay, hide screen 1 and show screen 2
                setTimeout(() => {
                    // Fade out screen 1
                    screen1.classList.add('fade-out');
                    
                    setTimeout(() => {
                        // Completely hide screen 1
                        screen1.style.display = 'none';
                        screen1.classList.remove('flex'); // Remove tailwind flex class if active
                        
                        // Show screen 2 and fade it in
                        screen2.classList.remove('hidden');
                        screen2.classList.add('fade-in');
                        
                        // 3. Bloom the flowers with staggered delays
                        flowers.forEach((flower, index) => {
                            setTimeout(() => {
                                flower.classList.add('bloom');
                            }, 400 + (index * 250)); // Stagger effect
                        });

                        // 4. Start falling petals
                        startPetals();
                        
                    }, 600); // Wait for fade-out to finish
                }, 800); // Wait for gift shaking to finish
            }

            // Bind click events
            btnOpen.addEventListener('click', openGift);
            giftElement.addEventListener('click', openGift);

            // Function to generate falling petals dynamically
            function startPetals() {
                const colors = ['#FDE047', '#FACC15', '#EAB308', '#FEF08A'];
                const totalPetals = 35; // Number of petals falling simultaneously

                for (let i = 0; i < totalPetals; i++) {
                    const petal = document.createElement('div');
                    petal.classList.add('petal');
                    
                    // Randomize size, position, duration and delay
                    const size = Math.random() * 15 + 8; // 8px to 23px
                    const leftPos = Math.random() * 100; // 0vw to 100vw
                    const animDelay = Math.random() * 5; // 0s to 5s
                    const animDuration = Math.random() * 4 + 4; // 4s to 8s
                    const color = colors[Math.floor(Math.random() * colors.length)];

                    petal.style.width = `${size}px`;
                    petal.style.height = `${size}px`;
                    petal.style.left = `${leftPos}vw`;
                    petal.style.animationDelay = `${animDelay}s`;
                    petal.style.animationDuration = `${animDuration}s`;
                    petal.style.backgroundColor = color;

                    // Append to screen 2
                    screen2.appendChild(petal);
                }
            }
        });
    </script>
</body>
</html>
