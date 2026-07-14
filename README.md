<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>𝓔𝓽𝓮𝓻𝓷𝓪layout 🖤 我們的專屬空間</title>
    <style>
        :root {
            --bg-dark: #0a0a0c;
            --panel-bg: rgba(22, 22, 26, 0.75);
            --border-color: rgba(255, 143, 163, 0.15);
            --border-glow: rgba(255, 143, 163, 0.4);
            --text-gold-pink: #fbccd4;
            --accent-pink: #ff8fa3;
            --deep-pink: #da7b93;
            --text-muted: #8e8e93;
            --white: #ffffff;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-dark);
            background-image: 
                radial-gradient(at 20% 20%, rgba(218, 123, 147, 0.15) 0px, transparent 50%),
                radial-gradient(at 80% 80%, rgba(255, 143, 163, 0.1) 0px, transparent 50%);
            background-attachment: fixed;
            color: var(--white);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            padding: 30px 15px;
        }

        /* 容器與毛玻璃特效 */
        .app-container {
            width: 100%;
            max-width: 480px;
            background: var(--panel-bg);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--border-color);
            border-radius: 32px;
            padding: 30px 24px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.7);
            position: relative;
            overflow: hidden;
        }

        /* 頁面切換控制 */
        .view-panel {
            display: none;
            animation: fadeIn 0.4s ease-out forwards;
        }

        .view-panel.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* 高級感文字與排版 */
        h1.title {
            font-size: 1.8rem;
            font-weight: 300;
            letter-spacing: 3px;
            text-align: center;
            color: var(--text-gold-pink);
            margin-bottom: 8px;
            text-shadow: 0 0 10px rgba(255, 143, 163, 0.3);
        }

        .subtitle {
            font-size: 0.85rem;
            color: var(--text-muted);
            text-align: center;
            margin-bottom: 35px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        h2.section-title {
            font-size: 1.3rem;
            font-weight: 400;
            color: var(--accent-pink);
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* 精緻頂部導航 */
        .nav-header {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
        }

        .back-btn {
            background: transparent;
            border: 1px solid var(--border-color);
            color: var(--accent-pink);
            padding: 8px 16px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.3s;
        }

        .back-btn:hover {
            border-color: var(--accent-pink);
            background: rgba(255, 143, 163, 0.1);
        }

        /* 主選單按鈕 */
        .menu-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
        }

        .menu-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 20px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .menu-card:hover {
            border-color: var(--accent-pink);
            box-shadow: 0 0 15px rgba(255, 143, 163, 0.15);
            transform: scale(1.02);
            background: rgba(255, 255, 255, 0.05);
        }

        .menu-card .info h3 {
            font-size: 1.1rem;
            font-weight: 400;
            margin-bottom: 4px;
            color: white;
        }

        .menu-card .info p {
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .menu-card .arrow {
            color: var(--accent-pink);
            font-size: 1.2rem;
        }

        /* 輸入欄位高級感樣式 */
        .input-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            font-size: 0.85rem;
            color: var(--text-gold-pink);
            margin-bottom: 8px;
            letter-spacing: 1px;
        }

        input[type="text"], input[type="date"], select, textarea {
            width: 100%;
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid var(--border-color);
            border-radius: 14px;
            padding: 14px;
            color: white;
            font-size: 0.95rem;
            transition: all 0.3s;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--accent-pink);
            box-shadow: 0 0 10px rgba(255, 143, 163, 0.2);
        }

        /* 性別選擇鈕 */
        .gender-selector {
            display: flex;
            gap: 12px;
        }

        .gender-option {
            flex: 1;
            background: rgba(0, 0, 0, 0.4);
            border: 1px solid var(--border-color);
            padding: 14px;
            border-radius: 14px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.9rem;
        }

        .gender-option.active {
            background: linear-gradient(135deg, var(--deep-pink), var(--accent-pink));
            color: var(--bg-dark);
            font-weight: 600;
            border-color: transparent;
        }

        /* 情境題樣式 */
        .quiz-wrapper {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 20px;
            margin-bottom: 20px;
        }

        .quiz-q {
            font-size: 1rem;
            margin-bottom: 15px;
            color: #fff;
            line-height: 1.4;
        }

        .option-item {
            display: flex;
            align-items: center;
            background: rgba(0,0,0,0.2);
            border: 1px solid rgba(255,255,255,0.05);
            padding: 12px 16px;
            border-radius: 12px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .option-item:hover {
            border-color: rgba(255, 143, 163, 0.3);
        }

        .option-item input[type="radio"] {
            margin-right: 12px;
            accent-color: var(--accent-pink);
            transform: scale(1.1);
        }

        /* 高級感圓圈標籤 (Pill Tags) */
        .tag-container {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }

        .tag-pill {
            background: rgba(255, 143, 163, 0.06);
            border: 1px solid var(--border-color);
            color: var(--text-gold-pink);
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.85rem;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
        }

        .tag-pill.dislike {
            border-color: rgba(235, 94, 123, 0.4);
            color: #ffb3c1;
        }

        .tag-pill .remove-x {
            cursor: pointer;
            opacity: 0.6;
            font-weight: bold;
        }
        .tag-pill .remove-x:hover { opacity: 1; }

        /* 行動按鈕 */
        .action-btn {
            background: linear-gradient(135deg, var(--deep-pink), var(--accent-pink));
            color: var(--bg-dark);
            border: none;
            width: 100%;
            padding: 15px;
            border-radius: 16px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            letter-spacing: 1px;
            box-shadow: 0 4px 15px rgba(255, 143, 163, 0.2);
        }

        .action-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 143, 163, 0.4);
        }

        .btn-secondary {
            background: transparent;
            border: 1px solid var(--accent-pink);
            color: var(--accent-pink);
            margin-top: 10px;
        }
        .btn-secondary:hover { background: rgba(255,143,163,0.05); }

        /* 紀念日儀表板專區 */
        .dashboard-widget {
            background: linear-gradient(145deg, rgba(255,143,163,0.08), rgba(0,0,0,0));
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 20px;
            margin-bottom: 25px;
            text-align: center;
        }

        .days-counter {
            font-size: 2.2rem;
            font-weight: 300;
            color: var(--accent-pink);
            margin: 10px 0;
            font-family: 'Courier New', Courier, monospace;
        }

        /* 列印/匯出隱藏無用組件 */
        @media print {
            body { background: white; color: black; }
            .app-container { box-shadow: none; border: none; max-width: 100%; }
            .back-btn, .action-btn, .input-group, .add-tag-form { display: none !important; }
            .view-panel { display: block !important; }
        }
    </style>
</head>
<body>

<div class="app-container">

    <!-- ================= HOME VIEW ================= -->
    <div id="view-home" class="view-panel active">
        <h1 class="title">𝓔𝓽𝓮𝓻𝓷𝓪𝓵 𝓛𝓸𝓿𝓮</h1>
        <div class="subtitle">我們的專屬默契空間</div>

        <!-- 儀表板：交往天數與紀念日 -->
        <div class="dashboard-widget">
            <p style="font-size: 0.85rem; color: var(--text-muted);">我們已經攜手走過</p>
            <div class="days-counter" id="display-days">520 Days</div>
            <p id="display-anniversary" style="font-size: 0.8rem; color: var(--text-gold-pink);">紀念日：2024.02.14</p>
        </div>

        <!-- 選單功能鈕 -->
        <div class="menu-grid">
            <div class="menu-card" onclick="switchView('view-about')">
                <div class="info">
                    <h3>關於我</h3>
                    <p>設定你的性別、星座與靈魂特質</p>
                </div>
                <div class="arrow">→</div>
            </div>

            <div class="menu-card" onclick="switchView('view-quiz')">
                <div class="info">
                    <h3>戀愛情境題</h3>
                    <p>吵架、報備、見面頻率與社交核心考驗</p>
                </div>
                <div class="arrow">→</div>
            </div>

            <div class="menu-card" onclick="switchView('view-hobbies')">
                <div class="info">
                    <h3>興趣愛好庫</h3>
                    <p>分類收藏你的運動、追劇與生活日常</p>
                </div>
                <div class="arrow">→</div>
            </div>

            <div class="menu-card" onclick="switchView('view-bounds')">
                <div class="info">
                    <h3>相處雷區與喜好</h3>
                    <p>食物偏好與相處時的加分與扣分項</p>
                </div>
                <div class="arrow">→</div>
            </div>

            <div class="menu-card" onclick="switchView('view-couple')">
                <div class="info">
                    <h3>情侶聯結與回顧</h3>
                    <p>天數設定、悄悄話與檔案導出 PDF</p>
                </div>
                <div class="arrow">→</div>
            </div>
        </div>
    </div>


    <!-- ================= ABOUT VIEW ================= -->
    <div id="view-about" class="view-panel">
        <div class="nav-header">
            <button class="back-btn" onclick="switchView('view-home')">← 返回</button>
        </div>
        <h2 class="section-title">✨ 關於我</h2>
        
        <div class="input-group">
            <label>我的性別</label>
            <div class="gender-selector">
                <div class="gender-option" id="g-male" onclick="setGender('男生')">♂ 男生</div>
                <div class="gender-option" id="g-female" onclick="setGender('女生')">♀ 女生</div>
            </div>
        </div>

        <div class="input-group">
            <label>個人星座</label>
            <input type="text" id="input-star" placeholder="如：天蠍座">
        </div>

        <div class="input-group">
            <label>MBTI 人格</label>
            <input type="text" id="input-mbti" placeholder="如：INFJ">
        </div>

        <div class="input-group">
            <label>個人特質描述</label>
            <textarea id="input-traits" rows="3" placeholder="用幾句話形容獨一無二的你..."></textarea>
        </div>
        
        <button class="action-btn" onclick="switchView('view-home')">儲存設定</button>
    </div>


    <!-- ================= QUIZ VIEW ================= -->
    <div id="view-quiz" class="view-panel">
        <div class="nav-header">
            <button class="back-btn" onclick="switchView('view-home')">← 返回</button>
        </div>
        <h2 class="section-title">🧩 戀愛情境題</h2>
        
        <div id="quiz-list">
            <!-- Q1 -->
            <div class="quiz-wrapper" data-question="如果今天你生氣了 你希望我怎麼做">
                <div class="quiz-q">Q1. 如果今天你生氣了 你希望我怎麼做？</div>
                <label class="option-item"><input type="radio" name="qa1" value="哄你"> 1. 哄你</label>
                <label class="option-item"><input type="radio" name="qa1" value="先理解你再討論問題"> 2. 先理解你再討論問題</label>
                <label class="option-item"><input type="radio" name="qa1" value="給你時間冷靜"> 3. 給你時間冷靜</label>
                <label class="option-item"><input type="radio" name="qa1" value="直接給出解決方案"> 4. 直接給出解決方案</label>
            </div>
            <!-- Q2 -->
            <div class="quiz-wrapper" data-question="你希望報備到什麼程度">
                <div class="quiz-q">Q2. 你希望報備到什麼程度？</div>
                <label class="option-item"><input type="radio" name="qa2" value="巨細靡遺"> 1. 巨細靡遺</label>
                <label class="option-item"><input type="radio" name="qa2" value="出門回家基本報備就好了"> 2. 出門回家基本報備就好了</label>
                <label class="option-item"><input type="radio" name="qa2" value="喜歡多分享一點"> 3. 喜歡多分享一點</label>
                <label class="option-item"><input type="radio" name="qa2" value="隨性一點 想講就講"> 4. 隨性一點 想講就講</label>
            </div>
            <!-- Q3 -->
            <div class="quiz-wrapper" data-question="見面頻率">
                <div class="quiz-q">Q3. 理想中的見面頻率？</div>
                <label class="option-item"><input type="radio" name="qa3" value="一週兩到三次"> 1. 一週兩到三次</label>
                <label class="option-item"><input type="radio" name="qa3" value="一週一次"> 2. 一週一次</label>
                <label class="option-item"><input type="radio" name="qa3" value="每天見面"> 3. 每天見面</label>
                <label class="option-item"><input type="radio" name="qa3" value="依實際情況調整"> 4. 依實際情況調整</label>
            </div>
            <!-- Q4 -->
            <div class="quiz-wrapper" data-question="社交局">
                <div class="quiz-q">Q4. 對於另一半的社交酒局？</div>
                <label class="option-item"><input type="radio" name="qa4" value="希望對方不要有酒局"> 1. 希望對方不要有酒局</label>
                <label class="option-item"><input type="radio" name="qa4" value="有酒局報備即可 不會想太多"> 2. 有酒局報備即可 不會想太多</label>
                <label class="option-item"><input type="radio" name="qa4" value="減少酒局"> 3. 減少酒局</label>
                <label class="option-item"><input type="radio" name="qa4" value="只有我在才能去酒局"> 4. 只有我在才能去酒局</label>
            </div>
        </div>

        <!-- 自由新增情境題 -->
        <div class="quiz-wrapper" style="background: rgba(255,143,163,0.03);">
            <label style="color: var(--accent-pink)">➕ 自訂情境選擇題</label>
            <input type="text" id="custom-q-title" placeholder="輸入自訂問題..." style="margin-bottom:8px;">
            <input type="text" id="custom-q-o1" placeholder="選項 1" style="margin-bottom:4px; padding:10px;">
            <input type="text" id="custom-q-o2" placeholder="選項 2" style="margin-bottom:8px; padding:10px;">
            <button class="action-btn btn-secondary" onclick="addCustomQuiz()">加入此題目</button>
        </div>

        <button class="action-btn" onclick="switchView('view-home')">確認儲存</button>
    </div>


    <!-- ================= HOBBIES VIEW ================= -->
    <div id="view-hobbies" class="view-panel">
        <div class="nav-header">
            <button class="back-btn" onclick="switchView('view-home')">← 返回</button>
        </div>
        <h2 class="section-title">🏃 興趣愛好庫</h2>

        <!-- 分類項目 -->
        <div class="input-group">
            <label>⚽ 運動方面</label>
            <div class="tag-container" id="container-sport">
                <div class="tag-pill">跑步 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill">健身 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill">打籃球 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
            </div>
        </div>

        <div class="input-group">
            <label>🍿 靜態/興趣</label>
            <div class="tag-container" id="container-interest">
                <div class="tag-pill">追劇 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill">烘焙 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
            </div>
        </div>

        <div class="quiz-wrapper" class="add-tag-form">
            <label>➕ 自行新增愛好選項</label>
            <select id="select-hobby-type" style="margin-bottom: 8px;">
                <option value="sport">運動方面</option>
                <option value="interest">靜態/興趣</option>
            </select>
            <input type="text" id="input-hobby-name" placeholder="輸入具體項目（例如：攀岩、密室逃脫）" style="margin-bottom: 8px;">
            <button class="action-btn btn-secondary" onclick="addHobbyTag()">新增愛好圈圈</button>
        </div>

        <button class="action-btn" onclick="switchView('view-home')">儲存返回</button>
    </div>


    <!-- ================= BOUNDS VIEW ================= -->
    <div id="view-bounds" class="view-panel">
        <div class="nav-header">
            <button class="back-btn" onclick="switchView('view-home')">← 返回</button>
        </div>
        <h2 class="section-title">🛑 相處雷區與喜好</h2>

        <div class="input-group">
            <label>❤️ 喜歡的食物</label>
            <input type="text" id="food-like" placeholder="例如：火鍋、草莓蛋糕">
        </div>

        <div class="input-group">
            <label>💔 討厭的食物</label>
            <input type="text" id="food-hate" placeholder="例如：香菜、芹菜">
        </div>

        <!-- 缺點/地雷雷區 -->
        <div class="input-group">
            <label>❌ 個人特別討厭的事（地雷雷區）</label>
            <div class="tag-container" id="container-dislike-tags">
                <div class="tag-pill dislike">吵架時：冷戰 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill dislike">吵架時：逃避問題 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill dislike">習慣：吃飯發出聲音 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
            </div>
            <div style="display:flex; gap:8px;">
                <input type="text" id="input-new-dislike" placeholder="例如：回訊息太敷衍" style="margin:0;">
                <button class="action-btn" style="width:auto; padding:12px 20px;" onclick="addBoundTag('dislike-tags', 'input-new-dislike', true)">+ 圈圈</button>
            </div>
        </div>

        <!-- 優秀/加分喜好 -->
        <div class="input-group">
            <label>⭕ 個人最期待/喜歡的事（甜蜜加分）</label>
            <div class="tag-container" id="container-like-tags">
                <div class="tag-pill">吵架時：立刻解決 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill">吵架時：哄我 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
                <div class="tag-pill">習慣：襪子內褲分開洗 <span class="remove-x" onclick="this.parentElement.remove()">×</span></div>
            </div>
            <div style="display:flex; gap:8px;">
                <input type="text" id="input-new-like" placeholder="例如：過節有儀式感" style="margin:0;">
                <button class="action-btn" style="width:auto; padding:12px 20px;" onclick="addBoundTag('like-tags', 'input-new-like', false)">+ 圈圈</button>
            </div>
        </div>

        <button class="action-btn" onclick="switchView('view-home')">儲存返回</button>
    </div>


    <!-- ================= COUPLE SYSTEM VIEW ================= -->
    <div id="view-couple" class="view-panel">
        <div class="nav-header">
            <button class="back-btn" onclick="switchView('view-home')">← 返回</button>
        </div>
        <h2 class="section-title">💍 情侶設定與資料導出</h2>

        <div class="input-group">
            <label>📅 設定我們的交往紀念日</label>
            <input type="date" id="config-anniversary" value="2024-02-14" onchange="updateAnniversary()">
        </div>

        <div class="input-group">
            <label>💌 想對另一半說的話（悄悄話）</label>
            <textarea id="couple-notes" rows="3" placeholder="寫下此時此刻想對他/她說的心心相印..."></textarea>
        </div>

        <div class="quiz-wrapper" style="border-style: dashed;">
            <label style="color:var(--accent-pink);">🔗 情侶虛擬綁定</label>
            <p style="font-size:0.75rem; color:var(--text-muted); margin-bottom:12px;">複製此連結發送給另一半，實現雲端雙向綁定查看（模擬機制）</p>
            <button class="action-btn btn-secondary" onclick="generateInviteLink()">點擊複製專屬邀請連結</button>
        </div>

        <!-- 導出與傳送 -->
        <button class="action-btn" onclick="triggerPDF()">🖨️ 輸出成 PDF 檔案 / 列印</button>
        <button class="action-btn btn-secondary" onclick="sendViaMail()">✉️ 透過 Email 寄送結果給對方</button>
    </div>

</div>

<script>
    let selectedGender = "尚未設定";
    let quizCount = 4;

    // 視窗換頁系統
    function switchView(viewId) {
        document.querySelectorAll('.view-panel').forEach(panel => {
            panel.classList.remove('active');
        });
        document.getElementById(viewId).classList.add('active');
        window.scrollTo(0,0);
    }

    // 性別按鈕切換
    function setGender(gender) {
        selectedGender = gender;
        document.getElementById('g-male').classList.remove('active');
        document.getElementById('g-female').classList.remove('active');
        if(gender === '男生') document.getElementById('g-male').classList.add('active');
        if(gender === '女生') document.getElementById('g-female').classList.add('active');
    }

    // 實時計算交往天數
    function updateAnniversary() {
        const dateVal = document.getElementById('config-anniversary').value;
        if(!dateVal) return;
        
        document.getElementById('display-anniversary').textContent = `紀念日：${dateVal.replace(/-/g, '.')}`;
        
        const annDate = new Date(dateVal);
        const today = new Date();
        const diffTime = Math.abs(today - annDate);
        const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
        
        document.getElementById('display-days').textContent = `${diffDays} Days`;
    }

    // 新增自訂情境選擇題
    function addCustomQuiz() {
        const title = document.getElementById('custom-q-title').value.trim();
        const o1 = document.getElementById('custom-q-o1').value.trim();
        const o2 = document.getElementById('custom-q-o2').value.trim();

        if(!title || !o1 || !o2) {
            alert('請至少完整輸入問題與前兩個選項！');
            return;
        }

        quizCount++;
        const listContainer = document.getElementById('quiz-list');
        const wrapper = document.createElement('div');
        wrapper.className = 'quiz-wrapper';
        wrapper.setAttribute('data-question', title);
        
        wrapper.innerHTML = `
            <div class="quiz-q">Q${quizCount}. ${title}？</div>
            <label class="option-item"><input type="radio" name="qa${quizCount}" value="${o1}"> 1. ${o1}</label>
            <label class="option-item"><input type="radio" name="qa${quizCount}" value="${o2}"> 2. ${o2}</label>
        `;
        listContainer.appendChild(wrapper);
        
        // 清空欄位
        document.getElementById('custom-q-title').value = '';
        document.getElementById('custom-q-o1').value = '';
        document.getElementById('custom-q-o2').value = '';
        alert('自訂題目已成功加入！');
    }

    // 新增興趣標籤 (Pill Tags)
    function addHobbyTag() {
        const type = document.getElementById('select-hobby-type').value;
        const name = document.getElementById('input-hobby-name').value.trim();
        if(!name) return;

        const container = document.getElementById(`container-${type}`);
        const pill = document.createElement('div');
        pill.className = 'tag-pill';
        pill.innerHTML = `${name} <span class="remove-x" onclick="this.parentElement.remove()">×</span>`;
        container.appendChild(pill);
        
        document.getElementById('input-hobby-name').value = '';
    }

    // 新增雷區與喜好標籤
    function addBoundTag(containerId, inputId, isDislike) {
        const inputEl = document.getElementById(inputId);
        const text = inputEl.value.trim();
        if(!text) return;

        const container = document.getElementById(`container-${containerId}`);
        const pill = document.createElement('div');
        pill.className = isDislike ? 'tag-pill dislike' : 'tag-pill';
        pill.innerHTML = `${text} <span class="remove-x" onclick="this.parentElement.remove()">×</span>`;
        container.appendChild(pill);
        
        inputEl.value = '';
    }

    // 生成虛擬情侶邀請連結
    function generateInviteLink() {
        const fakeToken = Math.random().toString(36).substring(2, 10).toUpperCase();
        const currentUrl = window.location.href.split('?')[0];
        const inviteUrl = `${currentUrl}?pairCode=${fakeToken}`;
        
        navigator.clipboard.writeText(inviteUrl).then(() => {
            alert(`🔗 邀請連結已複製！\n代碼為：[${fakeToken}]\n另一半點擊即可同步查看你設定的卡片狀態。`);
        }).catch(() => {
            alert(`請複製此網址傳給對方：\n${inviteUrl}`);
        });
    }

    // 彙整資料文字
    function compileAllData() {
        let quizSummary = "";
        document.querySelectorAll('#quiz-list .quiz-wrapper').forEach((el) => {
            const qText = el.getAttribute('data-question');
            const chosen = el.querySelector('input[type="radio"]:checked');
            const answer = chosen ? chosen.value : "未選擇";
            quizSummary += `- ${qText} : 【 ${answer} 】\n`;
        });

        const dataText = `💕 我們的專屬戀愛默契檔案 💕\n\n` +
            `【基本自我介紹】\n` +
            `• 性別: ${selectedGender}\n` +
            `• 星座: ${document.getElementById('input-star').value || '未填'}\n` +
            `• MBTI: ${document.getElementById('input-mbti').value || '未填'}\n` +
            `• 個人特質: ${document.getElementById('input-traits').value || '未填'}\n\n` +
            `【相處地雷與偏好】\n` +
            `• 喜歡的食物: ${document.getElementById('food-like').value || '未填'}\n` +
            `• 討厭的食物: ${document.getElementById('food-hate').value || '未填'}\n\n` +
            `【核心情境題選擇】\n${quizSummary}\n` +
            `【內心話悄悄話】\n"${document.getElementById('couple-notes').value || '無'}"`;
        
        return dataText;
    }

    // 觸發 PDF 檔案列印
    function triggerPDF() {
        alert("即將為您打開系統列印/存為PDF面板。請在列印選項中選擇「另存為 PDF」。");
        window.print();
    }

    // 發送 Email 模擬
    function sendViaMail() {
        const data = encodeURIComponent(compileAllData());
        const mailtoUrl = `mailto:?subject=我們的戀愛默契檔案報告&body=${data}`;
        window.location.href = mailtoUrl;
    }

    // 初始化交往天數
    window.onload = function() {
        updateAnniversary();
    };
</script>

</body>
</html>
