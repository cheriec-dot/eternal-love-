<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>𝓔𝓽𝓮𝓻𝓷𝓪𝓵 𝓛𝓸𝓿𝓮 🖤 我們的專屬空間</title>
    <style>
        :root {
            --bg-dark: #0a0a0c;
            --panel-bg: rgba(22, 22, 26, 0.75);
            --border-color: rgba(255, 143, 163, 0.15);
            --text-gold-pink: #fbccd4;
            --accent-pink: #ff8fa3;
            --deep-pink: #da7b93;
            --text-muted: #8e8e93;
            --white: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; -webkit-tap-highlight-color: transparent; }

        body {
            background-color: var(--bg-dark);
            background-image: radial-gradient(at 20% 20%, rgba(218, 123, 147, 0.15) 0px, transparent 50%), radial-gradient(at 80% 80%, rgba(255, 143, 163, 0.1) 0px, transparent 50%);
            background-attachment: fixed; color: var(--white); min-height: 100vh; display: flex; justify-content: center; align-items: flex-start; padding: 30px 15px;
        }

        .app-container {
            width: 100%; max-width: 480px; background: var(--panel-bg); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--border-color); border-radius: 32px; padding: 30px 24px; box-shadow: 0 20px 40px rgba(0, 0, 0, 0.7); overflow: hidden;
        }

        .view-panel { display: none; animation: fadeIn 0.4s ease-out forwards; }
        .view-panel.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        h1.title { font-size: 1.8rem; font-weight: 300; letter-spacing: 3px; text-align: center; color: var(--text-gold-pink); margin-bottom: 8px; text-shadow: 0 0 10px rgba(255, 143, 163, 0.3); }
        .subtitle { font-size: 0.85rem; color: var(--text-muted); text-align: center; margin-bottom: 35px; letter-spacing: 2px; }
        h2.section-title { font-size: 1.3rem; font-weight: 400; color: var(--accent-pink); margin-bottom: 25px; display: flex; align-items: center; gap: 10px; }

        .nav-header { display: flex; align-items: center; margin-bottom: 25px; }
        .back-btn { background: transparent; border: 1px solid var(--border-color); color: var(--accent-pink); padding: 8px 16px; border-radius: 50px; cursor: pointer; font-size: 0.85rem; transition: all 0.3s; }
        .back-btn:hover { border-color: var(--accent-pink); background: rgba(255, 143, 163, 0.1); }

        .menu-grid { display: grid; grid-template-columns: 1fr; gap: 16px; }
        .menu-card { background: rgba(255, 255, 255, 0.03); border: 1px solid var(--border-color); border-radius: 20px; padding: 20px; cursor: pointer; display: flex; justify-content: space-between; align-items: center; transition: all 0.3s; }
        .menu-card:hover { border-color: var(--accent-pink); transform: scale(1.02); background: rgba(255, 255, 255, 0.05); }
        .menu-card .info h3 { font-size: 1.1rem; font-weight: 400; margin-bottom: 4px; color: white; }
        .menu-card .info p { font-size: 0.8rem; color: var(--text-muted); }
        .menu-card .arrow { color: var(--accent-pink); font-size: 1.2rem; }

        .input-group { margin-bottom: 20px; }
        label { display: block; font-size: 0.85rem; color: var(--text-gold-pink); margin-bottom: 8px; letter-spacing: 1px; }
        input[type="text"], select, textarea { width: 100%; background: rgba(0, 0, 0, 0.4); border: 1px solid var(--border-color); border-radius: 14px; padding: 14px; color: white; font-size: 0.95rem; transition: all 0.3s; }
        input:focus, select:focus, textarea:focus { outline: none; border-color: var(--accent-pink); box-shadow: 0 0 10px rgba(255, 143, 163, 0.2); }

        /* 日期專用下拉選單 */
        .date-select-group { display: flex; gap: 8px; align-items: center; }
        .date-select-group select { flex: 1; padding: 12px; }

        .gender-selector { display: flex; gap: 12px; }
        .gender-option { flex: 1; background: rgba(0, 0, 0, 0.4); border: 1px solid var(--border-color); padding: 14px; border-radius: 14px; text-align: center; cursor: pointer; transition: all 0.3s; font-size: 0.9rem; }
        .gender-option.active { background: linear-gradient(135deg, var(--deep-pink), var(--accent-pink)); color: var(--bg-dark); font-weight: 600; border-color: transparent; }

        .action-btn { background: linear-gradient(135deg, var(--deep-pink), var(--accent-pink)); color: var(--bg-dark); border: none; width: 100%; padding: 15px; border-radius: 16px; font-size: 1rem; font-weight: 600; cursor: pointer; transition: all 0.3s; margin-top: 10px; }
        .action-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(255, 143, 163, 0.4); }

        .dashboard-widget { background: linear-gradient(145deg, rgba(255,143,163,0.08), rgba(0,0,0,0)); border: 1px solid var(--border-color); border-radius: 24px; padding: 20px; margin-bottom: 25px; text-align: center; }
        .days-counter { font-size: 2.2rem; font-weight: 300; color: var(--accent-pink); margin: 10px 0; font-family: 'Courier New', Courier, monospace; }
        
        .toast { position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); background: var(--accent-pink); color: black; padding: 10px 20px; border-radius: 50px; font-size: 0.9rem; font-weight: bold; opacity: 0; pointer-events: none; transition: opacity 0.3s; z-index: 1000; }
        .toast.show { opacity: 1; }
    </style>
</head>
<body>

<div class="app-container">
    <div id="toast" class="toast">✔️ 資料已自動儲存</div>

    <!-- 首頁 -->
    <div id="view-home" class="view-panel active">
        <h1 class="title">𝓔𝓽𝓮𝓻𝓷𝓪𝓵 𝓛𝓸𝓿𝓮</h1>
        <div class="subtitle">我們的專屬默契空間</div>

        <div class="dashboard-widget">
            <p style="font-size: 0.85rem; color: var(--text-muted);">我們已經攜手走過</p>
            <div class="days-counter" id="display-days">請先設定紀念日</div>
            <p id="display-anniversary" style="font-size: 0.8rem; color: var(--text-gold-pink);"></p>
        </div>

        <div class="menu-grid">
            <div class="menu-card" onclick="switchView('view-about')">
                <div class="info"><h3>關於我</h3><p>設定你的性別、星座與靈魂特質</p></div><div class="arrow">→</div>
            </div>
            <div class="menu-card" onclick="switchView('view-couple')">
                <div class="info"><h3>情侶設定</h3><p>設定交往天數與悄悄話</p></div><div class="arrow">→</div>
            </div>
        </div>
    </div>

    <!-- 關於我 -->
    <div id="view-about" class="view-panel">
        <div class="nav-header"><button class="back-btn" onclick="switchView('view-home')">← 返回</button></div>
        <h2 class="section-title">✨ 關於我</h2>
        
        <div class="input-group">
            <label>我的性別</label>
            <div class="gender-selector">
                <div class="gender-option" id="g-male" onclick="setGender('男生')">♂ 男生</div>
                <div class="gender-option" id="g-female" onclick="setGender('女生')">♀ 女生</div>
            </div>
        </div>
        <div class="input-group"><label>個人星座</label><input type="text" id="input-star" placeholder="如：天蠍座" oninput="saveDataLocally()"></div>
        <div class="input-group"><label>MBTI 人格</label><input type="text" id="input-mbti" placeholder="如：INFJ" oninput="saveDataLocally()"></div>
        <button class="action-btn" onclick="switchView('view-home')">確認</button>
    </div>

    <!-- 情侶設定與紀念日 -->
    <div id="view-couple" class="view-panel">
        <div class="nav-header"><button class="back-btn" onclick="switchView('view-home')">← 返回</button></div>
        <h2 class="section-title">💍 紀念日設定</h2>

        <div class="input-group">
            <label>📅 設定我們的交往紀念日</label>
            <div class="date-select-group">
                <select id="sel-year" onchange="updateAnniversary()"></select> <span style="color:var(--text-muted)">年</span>
                <select id="sel-month" onchange="updateAnniversary()"></select> <span style="color:var(--text-muted)">月</span>
                <select id="sel-day" onchange="updateAnniversary()"></select> <span style="color:var(--text-muted)">日</span>
            </div>
        </div>
        <div class="input-group"><label>💌 想對另一半說的話</label><textarea id="couple-notes" rows="3" placeholder="寫下想對他/她說的話..." oninput="saveDataLocally()"></textarea></div>
        <button class="action-btn" onclick="switchView('view-home')">確認儲存</button>
    </div>
</div>

<script>
    let selectedGender = "未設定";

    // 視窗切換
    function switchView(viewId) {
        document.querySelectorAll('.view-panel').forEach(panel => panel.classList.remove('active'));
        document.getElementById(viewId).classList.add('active');
        window.scrollTo(0,0);
    }

    // 性別設定
    function setGender(gender) {
        selectedGender = gender;
        document.getElementById('g-male').classList.remove('active');
        document.getElementById('g-female').classList.remove('active');
        if(gender === '男生') document.getElementById('g-male').classList.add('active');
        if(gender === '女生') document.getElementById('g-female').classList.add('active');
        saveDataLocally();
    }

    // 初始化日期下拉選單
    function initDateDropdowns() {
        const ySel = document.getElementById('sel-year');
        const mSel = document.getElementById('sel-month');
        const dSel = document.getElementById('sel-day');
        
        ySel.add(new Option('請選擇', ''));
        mSel.add(new Option('請選擇', ''));
        dSel.add(new Option('請選擇', ''));

        const currentYear = new Date().getFullYear();
        for(let i = currentYear; i >= 1990; i--) ySel.add(new Option(i, i));
        for(let i = 1; i <= 12; i++) mSel.add(new Option(i, i));
        for(let i = 1; i <= 31; i++) dSel.add(new Option(i, i));
    }

    // 計算交往天數
    function updateAnniversary() {
        const y = document.getElementById('sel-year').value;
        const m = document.getElementById('sel-month').value;
        const d = document.getElementById('sel-day').value;
        
        if(y && m && d) {
            document.getElementById('display-anniversary').textContent = `紀念日：${y}年${m}月${d}日`;
            const annDate = new Date(y, m - 1, d); // JS的月份是從0開始算的
            const today = new Date();
            
            const diffTime = today - annDate;
            if(diffTime < 0) {
                document.getElementById('display-days').textContent = "即將到來 ⏳";
            } else {
                const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));
                document.getElementById('display-days').textContent = `${diffDays} Days`;
            }
        }
        saveDataLocally();
    }

    // ★ 自動存檔到本機記憶體 ★
    function saveDataLocally() {
        const data = {
            gender: selectedGender,
            star: document.getElementById('input-star').value,
            mbti: document.getElementById('input-mbti').value,
            notes: document.getElementById('couple-notes').value,
            annY: document.getElementById('sel-year').value,
            annM: document.getElementById('sel-month').value,
            annD: document.getElementById('sel-day').value
        };
        localStorage.setItem('MyCoupleApp_Data', JSON.stringify(data));
        
        // 顯示已儲存提示
        const toast = document.getElementById('toast');
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 1500);
    }

    // ★ 讀取本機記憶體 ★
    function loadDataLocally() {
        const saved = localStorage.getItem('MyCoupleApp_Data');
        if(saved) {
            const data = JSON.parse(saved);
            if(data.gender && data.gender !== '未設定') setGender(data.gender);
            if(data.star) document.getElementById('input-star').value = data.star;
            if(data.mbti) document.getElementById('input-mbti').value = data.mbti;
            if(data.notes) document.getElementById('couple-notes').value = data.notes;
            if(data.annY) document.getElementById('sel-year').value = data.annY;
            if(data.annM) document.getElementById('sel-month').value = data.annM;
            if(data.annD) document.getElementById('sel-day').value = data.annD;
        }
    }

    window.onload = function() {
        initDateDropdowns();
        loadDataLocally();
        updateAnniversary();
    };
</script>
</body>
</html>
</html>
