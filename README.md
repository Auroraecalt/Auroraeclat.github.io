<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>秦晨綺 · Portfolio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">

    <style>
        /* ===== 色彩變數：配合照片的藍紫色調 (保留原設計風格) ===== */
        :root {
            --primary-accent: #a78bfa; /* 亮紫色 */
            --secondary-accent: #2dd4bf; /* 螢光青色 (做對比) */
            --highlight-pink: #f472b6; /* 呼應臉上的粉光 */
            
            --text-main: #ffffff;
            --text-dim: #cbd5e1; /* 淺灰 */
            
            --glass-bg: rgba(30, 41, 59, 0.65); /* 深色半透明背景 */
            --glass-border: rgba(255, 255, 255, 0.2);
            
            --font-heading: 'Playfair Display', serif;
            --font-body: 'Lato', sans-serif;
        }

        /* ===== 全局設定 ===== */
        * { box-sizing: border-box; }

        body {
            margin: 0;
            font-family: var(--font-body);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 24px;
            overflow-x: hidden;
            
            /* 背景：深藍夜色 + 強烈的霓虹光暈 */
            background-color: #0f172a; /* 深靛藍底色 */
            background-image: 
                radial-gradient(at 0% 0%, hsla(253,16%,7%,1) 0, transparent 50%), 
                radial-gradient(at 0% 0%, hsla(260, 100%, 60%, 0.4) 0, transparent 50%), /* 紫光 */
                radial-gradient(at 100% 0%, hsla(190, 100%, 50%, 0.3) 0, transparent 50%), /* 青光 */
                radial-gradient(at 100% 100%, hsla(320, 100%, 60%, 0.4) 0, transparent 50%), /* 粉光 */
                radial-gradient(at 0% 100%, hsla(240, 100%, 60%, 0.4) 0, transparent 50%); /* 藍光 */
            background-size: 150% 150%;
            animation: gradientMove 15s ease infinite;
            perspective: 1500px;
        }

        /* 增加一點雜訊質感，讓顏色看起來更像底片 */
        body::before {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            z-index: -1;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.6' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.04'/%3E%3C/svg%3E");
        }

        @keyframes gradientMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* ===== 卡片容器 ===== */
        .card-container {
            transform-style: preserve-3d;
            transition: transform 0.1s ease-out;
        }

        .resume-card {
            max-width: 1000px;
            width: 100%;
            /* 深色磨砂玻璃 */
            background: var(--glass-bg);
            backdrop-filter: blur(20px); 
            -webkit-backdrop-filter: blur(20px);
            border-radius: 24px;
            border: 1px solid var(--glass-border);
            box-shadow: 
                0 25px 50px -12px rgba(0, 0, 0, 0.5),
                inset 0 0 0 1px rgba(255, 255, 255, 0.1);
            display: grid;
            grid-template-columns: 320px 1fr;
            overflow: hidden;
            transform: translateZ(20px);
        }

        @media (max-width: 850px) {
            .resume-card {
                grid-template-columns: 1fr;
                max-width: 500px;
            }
            body { padding: 16px; perspective: none; }
            .card-container { transform: none !important; }
        }

        /* ===== 左側：形象區 ===== */
        .left-panel {
            /* 左側稍微再深一點，突出文字 */
            background: rgba(15, 23, 42, 0.4);
            padding: 40px 32px;
            border-right: 1px solid var(--glass-border);
            display: flex;
            flex-direction: column;
            gap: 24px; 
        }
        @media (max-width: 850px) {
            .left-panel { border-right: none; border-bottom: 1px solid var(--glass-border); }
        }

        .profile-text .name {
            font-family: var(--font-heading);
            font-size: 36px; /* 名字加大 */
            font-weight: 700;
            color: #fff;
            margin: 0 0 4px 0;
            /* 文字漸層 */
            background: linear-gradient(90deg, #fff, #a78bfa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .profile-text .role {
            font-size: 13px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            color: var(--secondary-accent); /* 青色對比 */
            margin-bottom: 12px;
            display: block;
        }

        .tagline {
            font-family: var(--font-heading);
            font-style: italic;
            font-size: 15px;
            color: var(--text-dim);
            line-height: 1.6;
            border-left: 3px solid var(--primary-accent);
            padding-left: 12px;
        }

        .art-pill {
            font-size: 12px;
            padding: 6px 14px;
            border-radius: 50px;
            border: 1px solid rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.05);
            color: var(--text-main);
            transition: 0.3s;
            margin-right: 4px;
            margin-bottom: 6px;
            display: inline-block;
        }
        .art-pill:hover {
            background: var(--primary-accent);
            border-color: var(--primary-accent);
            box-shadow: 0 0 15px var(--primary-accent); /* 發光效果 */
            color: #000;
            font-weight: bold;
        }

        .contact-list {
            margin-top: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 14px;
            color: var(--text-main);
            text-decoration: none;
            padding: 10px 16px;
            background: rgba(255,255,255,0.05);
            border-radius: 12px;
            transition: 0.2s;
            border: 1px solid transparent;
        }
        .contact-item:hover {
            background: rgba(255,255,255,0.15);
            border-color: var(--secondary-accent);
            transform: translateX(4px);
        }

        /* ===== 右側：內容區 ===== */
        .right-panel {
            padding: 40px;
            background: transparent;
        }
        @media (max-width: 850px) { .right-panel { padding: 24px; } }

        .section { margin-bottom: 36px; }
        .section:last-child { margin-bottom: 0; }

        .section-header {
            display: flex;
            align-items: baseline;
            gap: 12px;
            margin-bottom: 16px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            padding-bottom: 8px;
        }

        .section-title {
            font-family: var(--font-heading);
            font-size: 22px;
            font-weight: 700;
            color: var(--text-main);
            text-shadow: 0 0 20px rgba(167, 139, 250, 0.3);
        }

        /* 學校強調區 - 改成發光盒子 */
        .edu-badge {
            display: inline-flex;
            align-items: center;
            background: linear-gradient(135deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0.05) 100%);
            padding: 12px 20px;
            border-radius: 12px;
            border-left: 4px solid var(--highlight-pink); /* 粉色強調 */
            margin-bottom: 16px;
            width: 100%;
        }
        .edu-badge .school {
            font-weight: 700;
            font-size: 16px;
            margin-right: 12px;
            color: #fff;
        }
        .edu-badge .major {
            font-size: 14px;
            color: var(--text-dim);
            font-family: var(--font-heading);
            font-style: italic;
        }

        .description {
            font-size: 15px;
            line-height: 1.8;
            color: var(--text-dim);
        }

        /* 專案卡片 */
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }
        @media (max-width: 600px) { .grid-2 { grid-template-columns: 1fr; } }

        .item-card {
            background: rgba(255, 255, 255, 0.03);
            padding: 18px;
            border-radius: 16px;
            transition: all 0.3s ease;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .item-card:hover {
            transform: translateY(-4px);
            background: rgba(255, 255, 255, 0.1);
            border-color: var(--primary-accent);
            box-shadow: 0 10px 30px -10px rgba(167, 139, 250, 0.3);
        }

        .item-title {
            font-family: var(--font-heading);
            font-weight: 700;
            font-size: 16px;
            margin-bottom: 4px;
            color: #fff;
        }
        .item-sub {
            font-size: 11px;
            text-transform: uppercase;
            color: var(--secondary-accent);
            font-weight: 700;
            margin-bottom: 10px;
            letter-spacing: 0.05em;
        }
        .item-desc {
            font-size: 13px;
            color: var(--text-dim);
            line-height: 1.5;
        }

        /* 列表 */
        .styled-list { list-style: none; padding: 0; margin: 0; }
        .styled-list li {
            position: relative;
            padding-left: 24px;
            margin-bottom: 10px;
            font-size: 14px;
            line-height: 1.6;
            color: var(--text-dim);
        }
        .styled-list li strong { color: #fff; }
        .styled-list li::before {
            content: '✦';
            position: absolute;
            left: 0; top: 1px;
            color: var(--highlight-pink);
            font-size: 14px;
            text-shadow: 0 0 5px var(--highlight-pink);
        }

        .footer-note {
            font-size: 12px;
            text-align: center;
            margin-top: 30px;
            color: rgba(255,255,255,0.3);
            font-family: var(--font-heading);
            font-style: italic;
        }
    </style>
</head>
<body>

    <div class="card-container" id="tiltElement">
        <div class="resume-card">
            
            <div class="left-panel">
                
                <div class="profile-text">
                    <h1 class="name">秦晨綺</h1>
                    <span class="role">Business & Tech Student</span>
                    <div class="tagline">
                        "把國際貿易、商管和語言練到可以發光的那種學生。"
                    </div>
                </div>

                <div style="margin-top: 12px;">
                    <div class="art-pill">✨ ESFP</div>
                    <div class="art-pill">🌏 語言愛好者</div>
                    <div class="art-pill">🚢 國際貿易</div> <div class="art-pill">📊 NDHU IB</div>
                </div>

                <div class="contact-list">
                    <a href="https://github.com/Auroraeclat" target="_blank" class="contact-item">
                        <span>💻</span> GitHub Profile
                    </a>
                    <a href="mailto:your-email@example.com" class="contact-item">
                        <span>✉️</span> Email Contact
                    </a>
                </div>
            </div>

            <div class="right-panel">
                
                <div class="section">
                    <div class="section-header">
                        <span class="section-title">About Me</span>
                    </div>
                    
                    <div class="edu-badge">
                        <span class="school">國立東華大學</span>
                        <span class="major">國際企業學系</span>
                    </div>

                    <div class="description">
                        <p>我是一個熱愛在邏輯與感性之間尋找平衡的 **ESFP**。在東華國企的訓練下，我專注於國際貿易的流程、規範與實務操作。我不僅僅是為了完成作業，而是喜歡把複雜的國際條約與市場動態拆解、重組，變成清晰易懂的洞察。</p> </div>
                </div>

                <div class="section">
                    <div class="section-header">
                        <span class="section-title">Focus Areas</span>
                    </div>
                    <div class="grid-2">
                        <div class="item-card">
                            <div class="item-title">國際貿易實務</div> <div class="item-sub">Incoterms & Logistics</div> <div class="item-desc">深入了解 Incoterms、L/C 與進出口報關流程，優化全球供應鏈的效率。</div> </div>
                        <div class="item-card">
                            <div class="item-title">CRM 與商管</div>
                            <div class="item-sub">Business Insight</div>
                            <div class="item-desc">分析 Social CRM 案例，探討企業如何透過數據與流程優化顧客關係。</div>
                        </div>
                        <div class="item-card">
                            <div class="item-title">財務分析</div>
                            <div class="item-sub">Financial Literacy</div>
                            <div class="item-desc">閱讀企業財報，利用 ROA/ROE 等比率分析經營成效。</div>
                        </div>
                        <div class="item-card">
                            <div class="item-title">語言與溝通</div>
                            <div class="item-sub">Expression</div>
                            <div class="item-desc">不只是考試，而是為了更精準地傳達思想與共感，連結更大的世界。</div>
                        </div>
                    </div>
                </div>

                <div class="section">
                    <div class="section-header">
                        <span class="section-title">Highlights</span>
                    </div>
                    <ul class="styled-list">
                        <li>**跨域整合：** 習慣將商管知識與貿易實務結合，看見不同學科背後的共同規律。</li>
                        <li>**資訊視覺化：** 擅長將財報數據或複雜概念，整理成條理分明的筆記與架構。</li>
                        <li>**團隊協作：** 作為 ESFP，我能敏銳察覺團隊氣氛，並在推動進度與關懷成員間取得平衡。</li>
                    </ul>
                </div>

                <div class="footer-note">
                    Designed by 秦晨綺 · National Dong Hwa University
                </div>

            </div>
        </div>
    </div>

    <script>
        // 3D 傾斜效果
        const card = document.getElementById('tiltElement');
        const container = document.querySelector('.card-container');

        document.addEventListener('mousemove', (e) => {
            if (window.innerWidth <= 850) return; 

            const xAxis = (window.innerWidth / 2 - e.pageX) / 45; // 稍微減緩移動速度
            const yAxis = (window.innerHeight / 2 - e.pageY) / 45;

            container.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg) translateZ(10px)`;
        });

        container.addEventListener('mouseenter', () => {
            card.style.transition = 'none';
        });

        container.addEventListener('mouseleave', () => {
            card.style.transition = 'transform 0.5s ease';
            container.style.transform = `rotateY(0deg) rotateX(0deg) translateZ(10px)`;
        });
    </script>
</body>
</html>
