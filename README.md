# fuyusou.project-<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>判断の美学 | 富裕層のための思考矯正プログラム</title>
    <meta name="description" content="情報のノイズを断ち、確実な未来を選ぶための判断力を養う3ヶ月間のプログラム。">
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&family=Shippori+Mincho:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'luxury-black': '#0a0a0a',
                        'luxury-gray': '#1a1a1a',
                        'luxury-gold': '#d4af37',
                        'luxury-gold-light': '#f3e5ab',
                        'luxury-text': '#e5e5e5',
                        'luxury-muted': '#a3a3a3',
                    },
                    fontFamily: {
                        'sans': ['"Noto Sans JP"', 'sans-serif'],
                        'serif': ['"Shippori Mincho"', 'serif'],
                    },
                    animation: {
                        'ken-burns': 'kenBurns 20s ease-out infinite alternate',
                        'fade-in-up': 'fadeInUp 1s ease-out forwards',
                        'pulse-gold': 'pulse 1.5s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                    },
                    keyframes: {
                        kenBurns: {
                            '0%': { transform: 'scale(1)' },
                            '100%': { transform: 'scale(1.1)' },
                        },
                        fadeInUp: {
                            '0%': { opacity: '0', transform: 'translateY(20px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        pulse: {
                            '0%, 100%': { opacity: '1' },
                            '50%': { opacity: '.5' }
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #0a0a0a;
            color: #e5e5e5;
            font-family: 'Noto Sans JP', sans-serif;
        }
        h1, h2, h3, .serif-font {
            font-family: 'Shippori Mincho', serif;
        }
        
        /* Scroll Animation Observer Classes */
        .reveal-on-scroll {
            opacity: 0;
            transform: translateY(30px);
            transition: all 1s cubic-bezier(0.16, 1, 0.3, 1);
            will-change: opacity, transform;
        }
        .reveal-on-scroll.is-visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Staggered delays for child elements */
        .delay-100 { transition-delay: 0.1s; }
        .delay-200 { transition-delay: 0.2s; }
        .delay-300 { transition-delay: 0.3s; }
        
        /* Custom Button Hover */
        .btn-gold {
            background: linear-gradient(135deg, #d4af37 0%, #b4941f 100%);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .btn-gold::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: 0.5s;
        }
        .btn-gold:hover::after {
            left: 100%;
        }
        .btn-gold:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 20px rgba(212, 175, 55, 0.4);
        }

        /* Image Overlay Gradient */
        .image-overlay-gradient {
            background: linear-gradient(to top, rgba(10,10,10,0.9) 0%, rgba(10,10,10,0.4) 50%, rgba(10,10,10,0.1) 100%);
        }

        /* Chat Specific Styling */
        #chat-window {
            z-index: 1000;
            right: 1.5rem;
            bottom: 6rem; /* Adjust based on chat button position */
            width: 90vw; /* Responsive width for mobile */
            max-width: 400px;
            height: 70vh;
            max-height: 600px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
            transform-origin: bottom right;
            transition: transform 0.3s ease-out, opacity 0.3s ease-out;
        }

        #chat-toggle {
            z-index: 1001;
            right: 1.5rem;
            bottom: 1.5rem;
            box-shadow: 0 5px 20px rgba(212, 175, 55, 0.6);
        }

        .chat-message-user {
            background-color: #d4af37;
            color: #0a0a0a;
            border-radius: 1rem 1rem 0.2rem 1rem;
        }

        .chat-message-ai {
            background-color: #1a1a1a;
            color: #e5e5e5;
            border-radius: 1rem 1rem 1rem 0.2rem;
            border: 1px solid #d4af3740;
        }

        .source-link {
            color: #d4af37;
            text-decoration: underline;
            font-size: 0.75rem;
        }
    </style>
</head>
<body class="antialiased leading-relaxed overflow-x-hidden">

    <!-- Header -->
    <header class="fixed w-full top-0 z-50 bg-luxury-black/80 backdrop-blur-md border-b border-white/5 transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
            <div class="serif-font text-xl tracking-widest text-luxury-gold flex items-center gap-2">
                <span class="text-2xl">❖</span> 審美眼
            </div>
            <!-- Navigation links are hidden on mobile to maintain a clean header -->
            <nav class="hidden md:flex items-center space-x-8">
                <a href="#concept" class="text-sm text-luxury-muted hover:text-luxury-gold transition-colors relative group">
                    概念
                    <span class="absolute -bottom-1 left-0 w-0 h-px bg-luxury-gold transition-all group-hover:w-full"></span>
                </a>
                <a href="#service" class="text-sm text-luxury-muted hover:text-luxury-gold transition-colors relative group">
                    内容
                    <span class="absolute -bottom-1 left-0 w-0 h-px bg-luxury-gold transition-all group-hover:w-full"></span>
                </a>
                <a href="#pricing" class="inline-block px-5 py-2 text-xs border border-luxury-gold/50 text-luxury-gold hover:bg-luxury-gold hover:text-luxury-black transition-all rounded-sm">
                    参加申し込み
                </a>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="relative h-screen min-h-[700px] flex items-center justify-center overflow-hidden">
        <!-- Background Image with Ken Burns Effect -->
        <div class="absolute inset-0 z-0">
            <img src="https://placehold.co/1920x1080/050505/d4af37?text=Geometric+Abstraction+Luxury+Gold" alt="幾何学的な抽象芸術の背景" class="w-full h-full object-cover opacity-60 animate-ken-burns">
            <div class="absolute inset-0 bg-gradient-to-b from-luxury-black/30 via-luxury-black/70 to-luxury-black"></div>
            <!-- Radial overlay for focus -->
            <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_transparent_0%,_#0a0a0a_100%)] opacity-80"></div>
        </div>

        <div class="relative z-10 max-w-5xl mx-auto px-6 text-center">
            <div class="reveal-on-scroll delay-100">
                <p class="text-luxury-gold tracking-[0.3em] mb-8 text-xs md:text-sm uppercase font-medium border-b border-luxury-gold/30 inline-block pb-2">For the Discerning Few</p>
            </div>
            <!-- Responsive Text Size Adjustments for H1 -->
            <h1 class="serif-font text-4xl sm:text-5xl md:text-7xl lg:text-8xl font-medium leading-tight mb-10 reveal-on-scroll delay-200">
                <span class="block text-white drop-shadow-lg">情報は、</span>
                <span class="block text-luxury-muted mt-2 text-3xl sm:text-4xl md:text-6xl">捨ててこそ価値になる</span>
            </h1>
            <p class="text-gray-300 text-base md:text-lg mb-12 max-w-2xl mx-auto leading-loose reveal-on-scroll delay-300 font-light">
                AI時代、増え続けるノイズに思考を奪われていませんか。<br>
                富裕層に必要なのは、情報の量ではなく<strong class="text-luxury-gold font-normal">「選別の質」</strong>。<br>
                静かなる判断力を取り戻す、3ヶ月間の思考矯正プログラム。
            </p>
            <div class="reveal-on-scroll delay-300">
                <a href="#pricing" class="inline-block btn-gold text-luxury-black px-8 py-3 md:px-12 md:py-4 rounded-sm font-bold tracking-widest text-sm md:text-base">
                    詳細を確認する
                </a>
            </div>
        </div>
        
        <!-- Scroll Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce opacity-50">
            <span class="text-luxury-muted text-xs tracking-widest">SCROLL</span>
            <div class="w-px h-12 bg-luxury-muted mx-auto mt-2"></div>
        </div>
    </section>

    <!-- Problem Section -->
    <section id="concept" class="py-20 md:py-32 bg-luxury-gray relative">
        <div class="max-w-6xl mx-auto px-6">
            <!-- Mobile: Image stacks above text -->
            <div class="grid md:grid-cols-2 gap-12 md:gap-20 items-center">
                <div class="reveal-on-scroll relative group order-2 md:order-1">
                    <div class="absolute -inset-4 bg-luxury-gold/20 opacity-0 group-hover:opacity-100 transition-opacity duration-700 blur-xl hidden md:block"></div>
                    <img src="https://placehold.co/800x1000/1a1a1a/e5e5e5?text=Minimalist+Executive+Office+View" alt="ミニマルで洗練された役員室からの眺め" class="relative w-full h-auto rounded-sm shadow-2xl grayscale brightness-75 group-hover:brightness-100 transition-all duration-700 border border-white/5 z-10">
                    <!-- Decorative Frame -->
                    <div class="absolute top-6 -right-6 w-full h-full border border-luxury-gold/30 -z-0 hidden md:block transition-transform duration-700 group-hover:translate-x-2 group-hover:-translate-y-2"></div>
                </div>
                
                <div class="reveal-on-scroll delay-200 order-1 md:order-2">
                    <h2 class="serif-font text-3xl md:text-5xl mb-8 md:mb-10 text-white leading-snug">
                        なぜ、<br>
                        <span class="text-luxury-gold">「勉強熱心」</span>な人ほど<br>
                        投資で失敗するのか？
                    </h2>
                    <div class="space-y-6 md:space-y-8 text-luxury-muted text-base md:text-lg font-light leading-relaxed">
                        <p>
                            年収1,000万を超え、社会的地位もある。本も読むし、ニュースも追っている。<br>
                            それなのに、いざ「自分の資産」のことになると、判断が鈍る。
                        </p>
                        <p class="border-l-2 border-luxury-gold pl-6 py-2 bg-luxury-black/30">
                            原因は知識不足ではありません。<br>
                            <span class="text-luxury-gold-light font-medium">「判断軸のズレ」</span>と<span class="text-luxury-gold-light font-medium">「情報の肥満」</span>です。
                        </p>
                        <p>
                            派手な成功話や、AIが生成したような無機質な予測に踊らされるのはもう終わりにしませんか。<br>
                            必要なのは、誰も見ていない本質的な一手を、「静かに」打つ胆力です。
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Target Audience (Text Based with Icons) -->
    <section class="py-16 md:py-24 bg-luxury-black border-y border-white/5 bg-[url('https://placehold.co/1920x800/0a0a0a/111111?text=Grid+Pattern')] bg-fixed bg-cover bg-blend-overlay">
        <div class="max-w-4xl mx-auto px-6 text-center mb-12 md:mb-16 reveal-on-scroll">
            <h2 class="serif-font text-2xl md:text-3xl mb-4">本プログラムが目指すもの</h2>
            <div class="w-16 h-0.5 bg-luxury-gold mx-auto mb-6"></div>
            <p class="text-luxury-muted">Target Audience</p>
        </div>

        <!-- Mobile: Two columns stack -->
        <div class="max-w-6xl mx-auto px-6 grid md:grid-cols-2 gap-6 md:gap-8">
            <!-- For You -->
            <div class="bg-luxury-gray/80 backdrop-blur-sm p-6 md:p-10 border border-luxury-gold/30 rounded-sm reveal-on-scroll hover:bg-luxury-gray transition-colors">
                <h3 class="serif-font text-xl md:text-2xl text-luxury-gold mb-6 md:mb-8 flex items-center">
                    <span class="flex items-center justify-center w-8 h-8 md:w-10 md:h-10 border border-luxury-gold rounded-full mr-4 text-lg md:text-xl">✦</span>
                    【向いている人】
                </h3>
                <ul class="space-y-4 md:space-y-5 text-luxury-text font-light text-sm md:text-base">
                    <li class="flex items-start group">
                        <span class="text-luxury-gold mr-3 mt-1 group-hover:scale-125 transition-transform">✓</span>
                        <span><strong class="text-white font-normal">正解探しに疲れた</strong>方</span>
                    </li>
                    <li class="flex items-start group">
                        <span class="text-luxury-gold mr-3 mt-1 group-hover:scale-125 transition-transform">✓</span>
                        <span>もう<strong class="text-white font-normal">騙される側に戻りたくない</strong>方</span>
                    </li>
                    <li class="flex items-start group">
                        <span class="text-luxury-gold mr-3 mt-1 group-hover:scale-125 transition-transform">✓</span>
                        <span>自分の<strong class="text-white font-normal">判断軸を育てたい</strong>方</span>
                    </li>
                    <li class="flex items-start group">
                        <span class="text-luxury-gold mr-3 mt-1 group-hover:scale-125 transition-transform">✓</span>
                        <span>考える力を<strong class="text-white font-normal">「資産」</strong>にしたい方</span>
                    </li>
                </ul>
            </div>

            <!-- Not For You -->
            <div class="bg-black/50 backdrop-blur-sm p-6 md:p-10 border border-white/5 rounded-sm opacity-80 reveal-on-scroll delay-100">
                <h3 class="serif-font text-xl md:text-2xl text-gray-500 mb-6 md:mb-8 flex items-center">
                    <span class="flex items-center justify-center w-8 h-8 md:w-10 md:h-10 border border-gray-600 rounded-full mr-4 text-lg md:text-xl">✕</span>
                    【向いていない人】
                </h3>
                <ul class="space-y-4 md:space-y-5 text-gray-400 font-light text-sm md:text-base">
                    <li class="flex items-start">
                        <span class="text-gray-600 mr-3 mt-1">・</span>
                        とにかく楽に稼ぎたい方
                    </li>
                    <li class="flex items-start">
                        <span class="text-gray-600 mr-3 mt-1">・</span>
                        誰かに「正解」を教えてほしい方
                    </li>
                    <li class="flex items-start">
                        <span class="text-gray-600 mr-3 mt-1">・</span>
                        判断を他人に委ねたい方
                    </li>
                    <li class="flex items-start">
                        <span class="text-gray-600 mr-3 mt-1">・</span>
                        絶対に失敗したくない（リスクを取りたくない）方
                    </li>
                </ul>
            </div>
        </div>

        <div class="max-w-2xl mx-auto text-center mt-10 md:mt-12 reveal-on-scroll delay-200">
            <p class="text-lg md:text-xl serif-font text-white border-y border-luxury-gold/20 py-4 md:py-6 inline-block">
                このプログラムは<br class="md:hidden">
                <span class="text-luxury-gold">「選ぶ側に立ちたい人」</span>専用です。
            </p>
        </div>
    </section>

    <!-- Service Content with Images -->
    <section id="service" class="py-20 md:py-32 relative bg-luxury-gray overflow-hidden">
        <!-- Abstract Background Shape -->
        <div class="absolute top-0 right-0 w-[800px] h-[800px] bg-luxury-gold/5 rounded-full blur-3xl -translate-y-1/2 translate-x-1/2 hidden md:block"></div>
        
        <div class="max-w-6xl mx-auto px-6 relative z-10">
            <div class="mb-12 md:mb-20 reveal-on-scroll text-center md:text-left">
                <span class="text-luxury-gold text-sm tracking-widest uppercase mb-4 block">Our Approach</span>
                <h2 class="serif-font text-3xl md:text-5xl mb-4 md:mb-6 text-white">「答え」ではなく<br>「視点」のインストール</h2>
                <p class="text-luxury-muted text-base md:text-lg max-w-2xl mx-auto md:mx-0">
                    顔出しなし。通話なし。テキストのみ。<br>
                    あなたの貴重な時間を奪わず、思考の最深部に直接アプローチします。
                </p>
            </div>

            <!-- Mobile: Three columns stack -->
            <div class="grid md:grid-cols-3 gap-6 md:gap-8">
                <!-- Feature 1 -->
                <div class="group bg-luxury-black border border-white/10 hover:border-luxury-gold/50 transition-all duration-500 overflow-hidden reveal-on-scroll hover:-translate-y-2">
                    <div class="h-48 overflow-hidden relative">
                         <img src="https://placehold.co/600x400/222222/d4af37?text=Data+Analysis+Monochrome+Chart" alt="モノクロームのデータ分析チャート" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700 opacity-80 group-hover:opacity-100">
                         <div class="absolute inset-0 image-overlay-gradient"></div>
                         <span class="absolute top-4 right-4 text-4xl font-serif text-luxury-gold/30">01</span>
                    </div>
                    <div class="p-6 md:p-8 relative">
                        <h3 class="serif-font text-lg md:text-xl mb-3 md:mb-4 text-white group-hover:text-luxury-gold transition-colors">実際の事象を分解</h3>
                        <p class="text-xs md:text-sm text-luxury-muted leading-6 md:leading-7">
                            今、世界で起きているニュースや、実際に持ち込まれた投資案件を題材に、「どこを見るべきか」「何がリスクか」をテキストで徹底解説します。抽象論ではなく、生きたケーススタディです。
                        </p>
                    </div>
                </div>

                <!-- Feature 2 -->
                <div class="group bg-luxury-black border border-white/10 hover:border-luxury-gold/50 transition-all duration-500 overflow-hidden reveal-on-scroll delay-100 hover:-translate-y-2">
                    <div class="h-48 overflow-hidden relative">
                         <img src="https://placehold.co/600x400/2a2a2a/d4af37?text=Elegant+Chess+Board+Focus" alt="焦点が合わされたエレガントなチェス盤" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700 opacity-80 group-hover:opacity-100">
                         <div class="absolute inset-0 image-overlay-gradient"></div>
                         <span class="absolute top-4 right-4 text-4xl font-serif text-luxury-gold/30">02</span>
                    </div>
                    <div class="p-6 md:p-8 relative">
                        <h3 class="serif-font text-lg md:text-xl mb-3 md:mb-4 text-white group-hover:text-luxury-gold transition-colors">判断軸の壁打ち</h3>
                        <p class="text-xs md:text-sm text-luxury-muted leading-6 md:leading-7">
                            「この案件、どう思う？」という疑問に対し、Yes/Noではなく、「どのようなロジックで判断すべきか」のフレームワークを提示します。次回から自分で判断できるようになることがゴールです。
                        </p>
                    </div>
                </div>

                <!-- Feature 3 -->
                <div class="group bg-luxury-black border border-white/10 hover:border-luxury-gold/50 transition-all duration-500 overflow-hidden reveal-on-scroll delay-200 hover:-translate-y-2">
                    <div class="h-48 overflow-hidden relative">
                         <img src="https://placehold.co/600x400/1e1e1e/d4af37?text=Zen+Garden+Minimal+Shadows" alt="静寂でミニマルな影の禅庭" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700 opacity-80 group-hover:opacity-100">
                         <div class="absolute inset-0 image-overlay-gradient"></div>
                         <span class="absolute top-4 right-4 text-4xl font-serif text-luxury-gold/30">03</span>
                    </div>
                    <div class="p-6 md:p-8 relative">
                        <h3 class="serif-font text-lg md:text-xl mb-3 md:mb-4 text-white group-hover:text-luxury-gold transition-colors">思考のズレを修正</h3>
                        <p class="text-xs md:text-sm text-luxury-muted leading-6 md:leading-7">
                            月2回の配信を通じ、あなたの脳内にある「大衆的な思考の癖」を削ぎ落とします。富裕層特有の、冷徹で合理的な思考回路へとチューニングを行います。
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section id="pricing" class="py-20 md:py-32 relative">
        <!-- Background Image -->
        <div class="absolute inset-0 z-0">
             <img src="https://placehold.co/1920x1080/080808/333333?text=Exclusive+Members+Lounge+Seating" alt="会員制ラウンジの豪華な座席" class="w-full h-full object-cover opacity-30">
             <div class="absolute inset-0 bg-luxury-black/90"></div>
        </div>

        <div class="relative z-10 max-w-3xl mx-auto px-6 text-center reveal-on-scroll">
            <h2 class="serif-font text-2xl md:text-4xl mb-10 md:mb-12 text-white">Program Detail</h2>
            
            <!-- Pricing Card -->
            <div class="bg-gradient-to-b from-luxury-gray/90 to-luxury-black/90 backdrop-blur-md border border-luxury-gold/30 p-8 md:p-20 relative overflow-hidden shadow-2xl rounded-sm group">
                <!-- Decoration -->
                <div class="absolute -top-20 -right-20 w-64 h-64 bg-luxury-gold/10 rounded-full blur-3xl group-hover:bg-luxury-gold/20 transition-all duration-1000 hidden md:block"></div>

                <h3 class="serif-font text-xl md:text-3xl text-luxury-text mb-2">3ヶ月集中 判断力強化プログラム</h3>
                <p class="text-luxury-muted text-xs md:text-sm mb-10 md:mb-12 tracking-widest">思考のノイズキャンセリング</p>

                <div class="flex justify-center items-baseline mb-10 md:mb-12 scale-100 group-hover:scale-105 transition-transform duration-500">
                    <span class="text-xl md:text-2xl text-luxury-gold mr-2 font-serif">¥</span>
                    <span class="text-5xl md:text-7xl font-serif text-luxury-gold font-medium">49,800</span>
                    <span class="text-xs md:text-sm text-luxury-muted ml-3">（税込）</span>
                </div>

                <div class="text-left max-w-sm mx-auto space-y-4 md:space-y-5 mb-10 md:mb-14 text-sm md:text-base border-t border-b border-white/10 py-8 md:py-10">
                    <div class="flex justify-between items-center">
                        <span class="text-luxury-muted">期間</span>
                        <span class="font-medium">3ヶ月間</span>
                    </div>
                    <div class="flex justify-between items-center">
                        <span class="text-luxury-muted">頻度</span>
                        <span class="font-medium">月2回 テキスト配信・解説</span>
                    </div>
                    <div class="flex justify-between items-center">
                        <span class="text-luxury-muted">形式</span>
                        <span class="font-medium">完全オンライン<span class="text-xs text-luxury-muted ml-1">（顔出し不要）</span></span>
                    </div>
                </div>

                <div class="space-y-4 md:space-y-6">
                    <a href="#" class="block w-full btn-gold text-luxury-black font-bold py-4 md:py-5 px-8 rounded-sm tracking-[0.1em] md:tracking-[0.2em] text-base md:text-lg shadow-lg text-center">
                        申し込む
                    </a>
                    <p class="text-xs text-luxury-muted opacity-70 leading-relaxed">
                        ※即決を促すための割引や、限定タイマー等は一切ございません。<br>
                        必要なタイミングで、冷静にご判断ください。
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ -->
    <section class="py-16 md:py-24 bg-luxury-black">
        <div class="max-w-3xl mx-auto px-6">
            <h2 class="serif-font text-xl md:text-2xl mb-10 md:mb-12 text-center text-luxury-muted tracking-widest">FAQ</h2>
            
            <div class="space-y-6 md:space-y-8 reveal-on-scroll">
                <div class="group">
                    <h3 class="text-luxury-gold mb-2 md:mb-3 text-base md:text-lg group-hover:pl-2 transition-all duration-300">Q. 投資初心者でも参加できますか？</h3>
                    <p class="text-luxury-muted text-xs md:text-sm leading-relaxed pl-0 group-hover:pl-2 transition-all duration-300">可能ですが、用語の解説などは行いません。「何を買えばいいか」を知りたい段階の方より、「ある程度の資金はあるが、騙されたくない・守りたい」というフェーズの方に最適化されています。</p>
                </div>
                <hr class="border-white/5">
                <div class="group">
                    <h3 class="text-luxury-gold mb-2 md:mb-3 text-base md:text-lg group-hover:pl-2 transition-all duration-300">Q. 個別の投資相談には乗ってもらえますか？</h3>
                    <p class="text-luxury-muted text-xs md:text-sm leading-relaxed pl-0 group-hover:pl-2 transition-all duration-300">法的な助言（投資顧問業に該当する行為）は行いません。あくまで「この案件をどう分解し、どう思考するか」というセカンドオピニオン的な壁打ち相手として機能します。</p>
                </div>
                <hr class="border-white/5">
                <div class="group">
                    <h3 class="text-luxury-gold mb-2 md:mb-3 text-base md:text-lg group-hover:pl-2 transition-all duration-300">Q. なぜテキストのみなのですか？</h3>
                    <p class="text-luxury-muted text-xs md:text-sm leading-relaxed pl-0 group-hover:pl-2 transition-all duration-300">お互いの時間を同期させないためです。また、テキストに残すことで論理の飛躍を防ぎ、後から何度でも思考プロセスを読み返すことが可能になります。</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Closing Message Section (New) -->
    <section class="py-20 md:py-32 bg-luxury-gray relative overflow-hidden border-t border-white/5">
        <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_center,_var(--tw-gradient-stops))] from-luxury-gray via-luxury-black to-luxury-black opacity-80"></div>
        
        <div class="max-w-3xl mx-auto px-6 relative z-10 text-center reveal-on-scroll">
            <h2 class="serif-font text-lg md:text-2xl text-luxury-gold mb-10 md:mb-12 tracking-widest">【最後に】</h2>
            
            <div class="space-y-6 md:space-y-8 font-serif text-base md:text-xl leading-loose text-gray-300">
                <p>
                    このページを読んで<br>
                    <span class="text-white">「気になるけど、まだ迷う」</span><br>
                    そう感じたなら、
                </p>
                <p class="py-3 md:py-4">
                    <strong class="text-luxury-gold-light font-normal border-b border-luxury-gold/30 pb-1">今日は申し込まなくて大丈夫です。</strong>
                </p>
                <p>
                    迷えるということ自体、<br>
                    あなたが<br>
                    <span class="text-white">判断できる側に来た証拠</span>だからです。
                </p>
                <p>
                    参加するかどうかは、<br>
                    あなたが決めてください。
                </p>
                <p class="text-xl md:text-3xl text-white pt-3 md:pt-4">
                    選ばされる側ではなく、<br>
                    <span class="text-luxury-gold">選ぶ側</span>として。
                </p>
            </div>

            <div class="mt-16 md:mt-20">
                <a href="#" class="inline-flex items-center group">
                    <div class="h-px w-8 md:w-12 bg-luxury-gold mr-3 md:mr-4 transition-all group-hover:w-16 md:group-hover:w-20"></div>
                    <span class="serif-font text-luxury-gold text-base md:text-lg tracking-widest group-hover:text-white transition-colors">▶ 申込はこちら</span>
                    <div class="h-px w-8 md:w-12 bg-luxury-gold ml-3 md:ml-4 transition-all group-hover:w-16 md:group-hover:w-20"></div>
                </a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 md:py-12 border-t border-white/5 bg-luxury-gray text-center relative z-10">
        <div class="max-w-6xl mx-auto px-6">
            <p class="serif-font text-luxury-gold text-xl md:text-2xl mb-4 md:mb-6">審美眼</p>
            <div class="flex justify-center space-x-6 md:space-x-8 text-xs text-luxury-muted mb-6 md:mb-8">
                <a href="#" class="hover:text-white transition-colors">特定商取引法に基づく表記</a>
                <a href="#" class="hover:text-white transition-colors">プライバシーポリシー</a>
            </div>
            <p class="text-xs text-luxury-muted/30 tracking-widest">&copy; 2026 Judgment Refinement Program. All Rights Reserved.</p>
        </div>
    </footer>

    <!-- Chat Bot UI -->
    <!-- Chat Window (Fixed, Hidden initially) -->
    <div id="chat-window" class="fixed hidden bg-luxury-black border border-luxury-gold/50 rounded-lg flex flex-col scale-0 opacity-0">
        <!-- Chat Header -->
        <div class="p-4 border-b border-luxury-gold/30 flex justify-between items-center">
            <div class="flex items-center">
                <span class="w-2 h-2 rounded-full bg-luxury-gold mr-2 animate-pulse"></span>
                <span class="text-sm font-medium text-luxury-gold">審美眼 AIアシスタント</span>
            </div>
            <button id="chat-close" class="text-luxury-muted hover:text-white transition-colors">
                <i data-lucide="x" class="w-5 h-5"></i>
            </button>
        </div>

        <!-- Chat Messages -->
        <div id="chat-messages" class="flex-grow p-4 overflow-y-auto space-y-4 text-sm scrollbar-thin scrollbar-thumb-luxury-gold/50 scrollbar-track-luxury-black">
            <!-- Initial AI Message -->
            <div class="flex justify-start">
                <div class="chat-message-ai p-3 max-w-[85%]">
                    <p>ようこそ。富裕層向けの思考矯正プログラムに関心をお持ちいただき光栄です。ご質問や、情報選別の考え方についてなど、お気軽にお尋ねください。</p>
                </div>
            </div>
        </div>

        <!-- Chat Input -->
        <form id="chat-form" class="p-4 border-t border-luxury-gold/30 flex items-center">
            <input type="text" id="chat-input" placeholder="質問を入力..." class="flex-grow bg-luxury-black border border-white/10 text-luxury-text p-3 rounded-l-sm focus:ring-1 focus:ring-luxury-gold focus:border-luxury-gold/50 outline-none placeholder-luxury-muted/50 text-sm" autocomplete="off" required>
            <button type="submit" id="chat-submit" class="btn-gold text-luxury-black px-4 py-3 rounded-r-sm transition-opacity disabled:opacity-50" disabled>
                <i data-lucide="send" class="w-5 h-5"></i>
            </button>
        </form>
    </div>

    <!-- Chat Bot Toggle Button -->
    <button id="chat-toggle" class="fixed w-14 h-14 rounded-full btn-gold flex items-center justify-center transition-transform duration-300 hover:scale-105">
        <i data-lucide="message-square" class="w-6 h-6 text-luxury-black" id="chat-toggle-icon"></i>
    </button>
    

    <!-- Animation and Chat Script -->
    <script>
        // Initialize Lucide Icons
        lucide.createIcons();

        // --- UI Logic ---
        const chatToggle = document.getElementById('chat-toggle');
        const chatWindow = document.getElementById('chat-window');
        const chatClose = document.getElementById('chat-close');
        
        const toggleChat = () => {
            const isHidden = chatWindow.classList.contains('hidden');
            if (isHidden) {
                chatWindow.classList.remove('hidden');
                setTimeout(() => {
                    chatWindow.classList.remove('scale-0', 'opacity-0');
                    chatWindow.classList.add('scale-100', 'opacity-100');
                    // Change icon to X when open
                    document.getElementById('chat-toggle-icon').outerHTML = '<i data-lucide="x" class="w-6 h-6 text-luxury-black" id="chat-toggle-icon"></i>';
                    lucide.createIcons();
                }, 10);
            } else {
                chatWindow.classList.remove('scale-100', 'opacity-100');
                chatWindow.classList.add('scale-0', 'opacity-0');
                setTimeout(() => {
                    chatWindow.classList.add('hidden');
                    // Change icon back to message when closed
                    document.getElementById('chat-toggle-icon').outerHTML = '<i data-lucide="message-square" class="w-6 h-6 text-luxury-black" id="chat-toggle-icon"></i>';
                    lucide.createIcons();
                }, 300); // Match transition duration
            }
        };

        chatToggle.addEventListener('click', toggleChat);
        chatClose.addEventListener('click', toggleChat);

        // --- Chat Bot API Logic ---
        const chatForm = document.getElementById('chat-form');
        const chatInput = document.getElementById('chat-input');
        const chatMessages = document.getElementById('chat-messages');
        const chatSubmit = document.getElementById('chat-submit');

        const apiKey = "";
        const chatApiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
        let chatHistory = [];
        let isSending = false;

        // Enable/Disable submit button based on input
        chatInput.addEventListener('input', () => {
            chatSubmit.disabled = chatInput.value.trim() === '' || isSending;
        });

        // Helper function to render messages
        const addMessage = (text, role, sources = []) => {
            const messageDiv = document.createElement('div');
            messageDiv.className = `flex ${role === 'user' ? 'justify-end' : 'justify-start'}`;

            const contentDiv = document.createElement('div');
            contentDiv.className = `p-3 max-w-[85%] text-sm ${role === 'user' ? 'chat-message-user' : 'chat-message-ai'}`;
            contentDiv.innerHTML = `<p class="whitespace-pre-wrap">${text}</p>`;

            // Add sources if available and it's an AI message
            if (role === 'ai' && sources.length > 0) {
                const sourceList = document.createElement('div');
                sourceList.className = 'mt-2 pt-2 border-t border-white/10 text-xs text-luxury-muted/70';
                sourceList.innerHTML = '<p class="mb-1 font-medium">参照元:</p>';
                
                sources.forEach((source, index) => {
                    if (source.uri && source.title) {
                        const link = document.createElement('a');
                        link.href = source.uri;
                        link.target = '_blank';
                        link.className = 'source-link block truncate';
                        link.textContent = `${index + 1}. ${source.title}`;
                        sourceList.appendChild(link);
                    }
                });
                contentDiv.appendChild(sourceList);
            }

            messageDiv.appendChild(contentDiv);
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight; // Auto scroll
            return contentDiv;
        };

        // LLM API Call
        const callGeminiAPI = async (query) => {
            const systemPrompt = "あなたは富裕層向けの思考矯正プログラムのAIアシスタントです。豪華で洗練されたトーンで、投資、判断力、またはプログラムに関する質問に答えてください。回答は日本語で丁寧に行ってください。";

            // Add user query to history for context
            chatHistory.push({ role: "user", parts: [{ text: query }] });
            
            const payload = {
                contents: chatHistory,
                tools: [{ "google_search": {} }],
                systemInstruction: {
                    parts: [{ text: systemPrompt }]
                }
            };

            let response;
            let retries = 0;
            const maxRetries = 3;

            while (retries < maxRetries) {
                try {
                    response = await fetch(chatApiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (response.status === 429) {
                        retries++;
                        const delay = Math.pow(2, retries) * 1000;
                        await new Promise(resolve => setTimeout(resolve, delay));
                        continue; // Retry
                    }

                    if (!response.ok) {
                        throw new Error(`API returned status ${response.status}`);
                    }

                    const result = await response.json();
                    
                    const candidate = result.candidates?.[0];
                    if (candidate && candidate.content?.parts?.[0]?.text) {
                        const text = candidate.content.parts[0].text;
                        
                        let sources = [];
                        const groundingMetadata = candidate.groundingMetadata;
                        if (groundingMetadata && groundingMetadata.groundingAttributions) {
                            sources = groundingMetadata.groundingAttributions
                                .map(attribution => ({
                                    uri: attribution.web?.uri,
                                    title: attribution.web?.title,
                                }))
                                .filter(source => source.uri && source.title);
                        }

                        // Add AI response to history
                        chatHistory.push({ role: "model", parts: [{ text: text }] });
                        return { text, sources };
                    } else {
                        throw new Error("Invalid response structure or content missing.");
                    }
                } catch (error) {
                    console.error("Gemini API Error:", error);
                    retries++;
                    if (retries >= maxRetries) {
                        return { text: "申し訳ございません。現在、システム側の問題で応答できません。時間をおいて再度お試しください。", sources: [] };
                    }
                    const delay = Math.pow(2, retries) * 1000;
                    await new Promise(resolve => setTimeout(resolve, delay));
                }
            }
        };

        // Handle Form Submission
        chatForm.addEventListener('submit', async (e) => {
            e.preventDefault();
            const userQuery = chatInput.value.trim();
            if (!userQuery || isSending) return;

            // 1. Lock UI
            isSending = true;
            chatInput.value = '';
            chatSubmit.disabled = true;
            
            // 2. Display User Message
            addMessage(userQuery, 'user');
            
            // 3. Display Loading Indicator
            const loadingMessage = addMessage('思考中...', 'ai');
            loadingMessage.innerHTML = `<span class="inline-block w-2 h-2 rounded-full bg-luxury-gold animate-pulse-gold mr-2"></span> 思考中...`;

            // 4. Call API
            const { text: aiResponseText, sources: aiSources } = await callGeminiAPI(userQuery);

            // 5. Update UI with AI Response
            loadingMessage.innerHTML = `<p class="whitespace-pre-wrap">${aiResponseText}</p>`;
            
            // Re-render sources if they exist
            if (aiSources.length > 0) {
                 // Remove loading text and re-add content with sources
                loadingMessage.innerHTML = ''; 
                const contentText = document.createElement('p');
                contentText.className = 'whitespace-pre-wrap';
                contentText.textContent = aiResponseText;
                loadingMessage.appendChild(contentText);

                const sourceList = document.createElement('div');
                sourceList.className = 'mt-2 pt-2 border-t border-white/10 text-xs text-luxury-muted/70';
                sourceList.innerHTML = '<p class="mb-1 font-medium">参照元:</p>';
                
                aiSources.forEach((source, index) => {
                    if (source.uri && source.title) {
                        const link = document.createElement('a');
                        link.href = source.uri;
                        link.target = '_blank';
                        link.className = 'source-link block truncate';
                        link.textContent = `${index + 1}. ${source.title}`;
                        sourceList.appendChild(link);
                    }
                });
                loadingMessage.appendChild(sourceList);
            }
            chatMessages.scrollTop = chatMessages.scrollHeight;

            // 6. Unlock UI
            isSending = false;
            chatSubmit.disabled = chatInput.value.trim() === '';
        });

        // --- General UI Script ---
        document.addEventListener('DOMContentLoaded', () => {
            const observerOptions = {
                root: null,
                rootMargin: '0px',
                threshold: 0.15
            };

            const observer = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('is-visible');
                        observer.unobserve(entry.target); // Run once
                    }
                });
            }, observerOptions);

            const revealElements = document.querySelectorAll('.reveal-on-scroll');
            revealElements.forEach(el => observer.observe(el));
            
            // Navbar scroll effect
            const navbar = document.getElementById('navbar');
            window.addEventListener('scroll', () => {
                if (window.scrollY > 50) {
                    navbar.classList.add('py-2', 'bg-luxury-black/95');
                    navbar.classList.remove('py-4', 'bg-luxury-black/80');
                } else {
                    navbar.classList.add('py-4', 'bg-luxury-black/80');
                    navbar.classList.remove('py-2', 'bg-luxury-black/95');
                }
            });
        });
    </script>
</body>
</html>
