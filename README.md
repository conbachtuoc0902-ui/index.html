<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>Người Que Diệt Zombie: 10 Trại & Đại Chiến Trùm Nguyên Mẫu</title>
  <style>
    * {
      box-sizing: border-box;
      user-select: none;
      -webkit-user-select: none;
      -webkit-tap-highlight-color: transparent;
    }

    :root {
      --bg-dark: #070913;
      --bg-card: #12172b;
      --bg-card-2: #19213d;
      --border: rgba(255, 255, 255, 0.12);
      --text: #f8fafc;
      --muted: #94a3b8;
      --accent: #38bdf8;
      --accent-2: #a855f7;
      --good: #22c55e;
      --warn: #f59e0b;
      --danger: #ef4444;
    }

    html, body {
      margin: 0;
      padding: 0;
      width: 100%;
      height: 100%;
      background: var(--bg-dark);
      color: var(--text);
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      overflow: hidden;
    }

    #app {
      position: relative;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      background: radial-gradient(circle at 50% 15%, #172042 0%, #090c18 65%, #05070e 100%);
    }

    /* SẢNH CHỜ */
    #lobbyScreen {
      position: relative;
      z-index: 10;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 18px 16px 22px;
      overflow-y: auto;
    }

    .top-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      z-index: 20;
    }

    .badge-pill {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: rgba(18, 23, 43, 0.9);
      border: 1px solid var(--border);
      padding: 7px 12px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 700;
    }

    .icon-btn {
      background: rgba(25, 33, 61, 0.95);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 8px 12px;
      font-size: 13px;
      font-weight: 700;
      cursor: pointer;
    }

    .icon-btn:active {
      transform: scale(0.96);
    }

    .hero-box {
      text-align: center;
      margin: 12px auto 10px;
      max-width: 540px;
    }

    .hero-tag {
      display: inline-block;
      font-size: 11px;
      letter-spacing: 1.2px;
      text-transform: uppercase;
      color: var(--accent);
      background: rgba(56, 189, 248, 0.14);
      border: 1px solid rgba(56, 189, 248, 0.35);
      padding: 4px 10px;
      border-radius: 999px;
      font-weight: 800;
      margin-bottom: 8px;
    }

    .hero-title {
      margin: 0;
      font-size: clamp(24px, 6vw, 38px);
      line-height: 1.15;
      font-weight: 900;
      text-shadow: 0 4px 24px rgba(56, 189, 248, 0.25);
    }

    .hero-sub {
      margin: 8px auto 0;
      font-size: 13px;
      color: var(--muted);
      line-height: 1.45;
      max-width: 460px;
    }

    .selected-class-card {
      margin: 10px auto;
      width: 100%;
      max-width: 500px;
      background: linear-gradient(145deg, rgba(25, 33, 61, 0.95), rgba(15, 20, 38, 0.95));
      border: 1px solid rgba(168, 85, 247, 0.35);
      border-radius: 18px;
      padding: 14px 16px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.35);
    }

    .class-header-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
    }

    .class-name {
      font-size: 18px;
      font-weight: 900;
    }

    .class-hp {
      font-size: 12px;
      font-weight: 800;
      color: #86efac;
      background: rgba(34, 197, 94, 0.14);
      border: 1px solid rgba(34, 197, 94, 0.35);
      padding: 3px 9px;
      border-radius: 999px;
    }

    .class-desc {
      margin: 6px 0 0;
      font-size: 12.5px;
      color: #cbd5e1;
      line-height: 1.45;
    }

    .lobby-actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      width: 100%;
      max-width: 500px;
      margin: 12px auto 0;
      z-index: 20;
    }

    .btn-primary {
      grid-column: 1 / -1;
      background: linear-gradient(135deg, #22c55e, #16a34a);
      color: #041309;
      border: none;
      border-radius: 16px;
      padding: 15px 18px;
      font-size: 17px;
      font-weight: 900;
      cursor: pointer;
      box-shadow: 0 8px 24px rgba(34, 197, 94, 0.35);
    }

    .btn-secondary {
      background: var(--bg-card-2);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 13px 14px;
      font-size: 14px;
      font-weight: 800;
      cursor: pointer;
    }

    .btn-primary:active,
    .btn-secondary:active {
      transform: scale(0.97);
    }

    .lobby-footer-note {
      text-align: center;
      font-size: 11.5px;
      color: var(--muted);
      margin-top: 12px;
    }

    /* MODAL */
    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(3, 5, 12, 0.82);
      backdrop-filter: blur(4px);
      z-index: 60;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 14px;
    }

    .modal-backdrop.open {
      display: flex;
    }

    .modal-box {
      width: 100%;
      max-width: 540px;
      max-height: 88vh;
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 16px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      overflow-y: auto;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.65);
    }

    .modal-head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .modal-title {
      margin: 0;
      font-size: 18px;
      font-weight: 900;
    }

    .close-btn {
      background: rgba(255, 255, 255, 0.08);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 6px 11px;
      font-weight: 800;
      cursor: pointer;
    }

    .class-list {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .class-item {
      background: var(--bg-card-2);
      border: 1px solid var(--border);
      border-radius: 15px;
      padding: 12px;
      display: flex;
      flex-direction: column;
      gap: 7px;
    }

    .class-item.active {
      border-color: var(--accent);
      box-shadow: 0 0 0 1px rgba(56, 189, 248, 0.4);
    }

    .class-item-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
    }

    .class-item-actions {
      display: flex;
      gap: 8px;
      margin-top: 2px;
    }

    .small-btn {
      border: none;
      border-radius: 10px;
      padding: 8px 12px;
      font-size: 12.5px;
      font-weight: 800;
      cursor: pointer;
    }

    .small-btn.pick {
      background: var(--accent);
      color: #06131f;
    }

    .small-btn.unlock {
      background: var(--warn);
      color: #1a1002;
    }

    .small-btn.disabled {
      background: rgba(255, 255, 255, 0.08);
      color: var(--muted);
      cursor: not-allowed;
    }

    .resume-banner {
      background: rgba(56, 189, 248, 0.14);
      border: 1px solid rgba(56, 189, 248, 0.45);
      border-radius: 14px;
      padding: 11px 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .lv-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
    }

    .lv-btn {
      background: var(--bg-card-2);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 10px 8px;
      color: var(--text);
      font-weight: 800;
      font-size: 12.5px;
      text-align: center;
      cursor: pointer;
      display: flex;
      flex-direction: column;
      gap: 3px;
    }

    .lv-btn.boss-lv {
      grid-column: 1 / -1;
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.25), rgba(239, 68, 68, 0.22));
      border-color: rgba(239, 68, 68, 0.45);
    }

    .lv-btn.cleared {
      border-color: rgba(34, 197, 94, 0.55);
    }

    .lv-btn.locked {
      opacity: 0.45;
      cursor: not-allowed;
    }

    .lv-sub {
      font-size: 10.5px;
      font-weight: 700;
      color: var(--muted);
    }

    /* MÀN HÌNH CHƠI GAME */
    #gameScreen {
      position: relative;
      width: 100%;
      height: 100%;
      display: none;
      flex-direction: column;
    }

    #gameScreen.active {
      display: flex;
    }

    #gameCanvas {
      width: 100%;
      height: 100%;
      display: block;
    }

    .hud-top {
      position: absolute;
      top: 10px;
      left: 10px;
      right: 10px;
      z-index: 15;
      display: flex;
      flex-direction: column;
      gap: 8px;
      pointer-events: none;
    }

    .hud-row {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 8px;
    }

    .hud-panel {
      pointer-events: auto;
      background: rgba(12, 16, 32, 0.86);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 8px 11px;
      min-width: 195px;
      max-width: 310px;
      flex: 1;
    }

    .hud-title-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 6px;
      font-size: 12px;
      font-weight: 900;
      margin-bottom: 5px;
    }

    .bar-wrap {
      width: 100%;
      height: 10px;
      background: rgba(255, 255, 255, 0.12);
      border-radius: 999px;
      overflow: hidden;
    }

    .bar-fill.hp {
      height: 100%;
      background: linear-gradient(90deg, #ef4444, #f59e0b, #22c55e);
      transition: width 0.12s linear;
    }

    .bar-fill.boss {
      height: 100%;
      background: linear-gradient(90deg, #dc2626, #a855f7);
      transition: width 0.12s linear;
    }

    .bar-fill.water {
      height: 100%;
      background: linear-gradient(90deg, #0284c7, #38bdf8);
      transition: width 0.1s linear;
    }

    .hud-controls-right {
      pointer-events: auto;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .mini-btn {
      background: rgba(18, 23, 43, 0.92);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 11px;
      padding: 7px 10px;
      font-size: 12px;
      font-weight: 800;
      cursor: pointer;
    }

    .banner-toast {
      align-self: center;
      background: rgba(15, 23, 42, 0.92);
      border: 1px solid rgba(56, 189, 248, 0.45);
      color: #f8fafc;
      padding: 6px 14px;
      border-radius: 999px;
      font-size: 12.5px;
      font-weight: 800;
      opacity: 0;
      transition: opacity 0.2s ease;
    }

    .banner-toast.show {
      opacity: 1;
    }

    /* ĐIỀU KHIỂN DƯỚI */
    .hud-bottom {
      position: absolute;
      left: 10px;
      right: 10px;
      bottom: 12px;
      z-index: 15;
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      gap: 10px;
      pointer-events: none;
    }

    .move-pad {
      pointer-events: auto;
      display: flex;
      gap: 8px;
    }

    .pad-btn {
      width: 56px;
      height: 56px;
      border-radius: 16px;
      background: rgba(18, 23, 43, 0.88);
      border: 1px solid var(--border);
      color: var(--text);
      font-size: 20px;
      font-weight: 900;
      cursor: pointer;
    }

    .pad-btn:active {
      background: rgba(56, 189, 248, 0.28);
      transform: scale(0.95);
    }

    .skill-pad {
      pointer-events: auto;
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-end;
      gap: 8px;
      max-width: 72%;
    }

    .act-btn {
      border: none;
      border-radius: 15px;
      padding: 11px 13px;
      font-size: 12.5px;
      font-weight: 900;
      cursor: pointer;
      color: #fff;
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.35);
    }

    .act-btn.attack {
      background: linear-gradient(135deg, #ef4444, #dc2626);
      padding: 13px 16px;
      font-size: 13.5px;
    }

    .act-btn.skill {
      background: linear-gradient(135deg, #6366f1, #8b5cf6);
    }

    .act-btn.utility {
      background: linear-gradient(135deg, #0ea5e9, #0284c7);
    }

    .act-btn:disabled {
      opacity: 0.45;
      cursor: not-allowed;
    }

    /* THƯ TWIST & KẾT THÚC */
    #endingOverlay {
      position: fixed;
      inset: 0;
      z-index: 70;
      background: rgba(4, 6, 14, 0.88);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 14px;
    }

    #endingOverlay.open {
      display: flex;
    }

    .letter-card {
      width: 100%;
      max-width: 480px;
      background: #fffbeb;
      color: #1e293b;
      border: 3px solid #f59e0b;
      border-radius: 22px;
      padding: 18px;
      box-shadow: 0 24px 60px rgba(0, 0, 0, 0.7);
    }

    .letter-badge {
      display: inline-block;
      background: #fee2e2;
      color: #b91c1c;
      font-size: 11px;
      font-weight: 900;
      padding: 3px 9px;
      border-radius: 999px;
      float: right;
    }

    .letter-quote {
      margin: 12px 0;
      padding: 14px;
      background: #fef3c7;
      border: 2px dashed #d97706;
      border-radius: 14px;
      font-size: 16px;
      font-weight: 900;
      text-align: center;
      color: #0f172a;
    }

    .stat-box {
      background: #0f172a;
      color: #f8fafc;
      border-radius: 14px;
      padding: 12px;
      font-size: 13px;
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 6px 12px;
      margin-bottom: 14px;
    }

    .end-btn-green {
      width: 100%;
      background: #16a34a;
      color: #fff;
      border: none;
      border-radius: 13px;
      padding: 12px;
      font-size: 14px;
      font-weight: 900;
      cursor: pointer;
      margin-bottom: 8px;
    }

    .end-btn-dark {
      width: 100%;
      background: #1e293b;
      color: #fff;
      border: none;
      border-radius: 13px;
      padding: 12px;
      font-size: 14px;
      font-weight: 800;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="app">
    <!-- SẢNH CHỜ -->
    <section id="lobbyScreen">
      <div class="top-bar">
        <div class="badge-pill">🥫 Đồ Hộp: <span id="lobbySupplies">0</span></div>
        <div style="display:flex;gap:8px;">
          <button type="button" class="icon-btn" id="btnSound">🔊 Âm thanh: Bật</button>
          <button type="button" class="icon-btn" id="btnResetSave">🗑️ Reset</button>
        </div>
      </div>

      <div class="hero-box">
        <span class="hero-tag">Đêm Tối • 10 Trạm • Trùm Nguyên Mẫu</span>
        <h1 class="hero-title">NGƯỜI QUE DIỆT ZOMBIE</h1>
        <p class="hero-sub">
          Vượt 10 trạm trú ẩn (7 trại tiếp tế, 3 trại giải cứu đồng minh AI tối đa 3 người), nhặt khiên đấu Trùm Zombie Nguyên Mẫu 1.000 HP và khám phá bí mật cuối lâu đài.
        </p>
      </div>

      <div class="selected-class-card">
        <div class="class-header-row">
          <div class="class-name" id="lobbyClassName">Người Sống Sót</div>
          <div class="class-hp" id="lobbyClassHp">150 HP</div>
        </div>
        <p class="class-desc" id="lobbyClassDesc"></p>
      </div>

      <div class="lobby-actions">
        <button type="button" class="btn-primary" id="btnPlay">▶️ BẮT ĐẦU HÀNH TRÌNH</button>
        <button type="button" class="btn-secondary" id="btnOpenLv">🗺️ CHỌN LV</button>
        <button type="button" class="btn-secondary" id="btnOpenClasses">🎭 CLASSES</button>
      </div>

      <div class="lobby-footer-note" id="lobbyProgressText">Tiến độ: Trạm 1/10</div>
    </section>

    <!-- MÀN HÌNH GAME -->
    <section id="gameScreen">
      <canvas id="gameCanvas"></canvas>

      <div class="hud-top">
        <div class="hud-row">
          <div class="hud-panel">
            <div class="hud-title-line">
              <span id="hudClassLabel">Người Sống Sót</span>
              <span id="hudAllyLabel">🤝 0/3 Đồng Minh</span>
            </div>
            <div style="display:flex;justify-content:space-between;font-size:11.5px;font-weight:800;margin-bottom:4px;">
              <span id="hudStageLabel">Trạm 1 / 10</span>
              <span id="hudHpText">150 / 150 HP</span>
            </div>
            <div class="bar-wrap">
              <div class="bar-fill hp" id="hudHpBar" style="width:100%;"></div>
            </div>
            <div id="hudWaterWrap" style="display:none;margin-top:6px;">
              <div style="display:flex;justify-content:space-between;font-size:11px;font-weight:800;margin-bottom:3px;">
                <span>💧 Bình Nước Laser</span>
                <span id="hudWaterText">100%</span>
              </div>
              <div class="bar-wrap" style="height:7px;">
                <div class="bar-fill water" id="hudWaterBar" style="width:100%;"></div>
              </div>
            </div>
          </div>

          <div class="hud-controls-right">
            <button type="button" class="mini-btn" id="btnPauseLobby">🏠 Sảnh</button>
            <button type="button" class="mini-btn" id="btnIngameSound">🔊</button>
          </div>
        </div>

        <div class="hud-panel" id="hudBossPanel" style="display:none;border-color:rgba(239,68,68,0.55);">
          <div class="hud-title-line">
            <span style="color:#fca5a5;">🦾 TRÙM ZOMBIE NGUYÊN MẪU</span>
            <span id="hudBossHpText">1000 / 1000 HP</span>
          </div>
          <div class="bar-wrap">
            <div class="bar-fill boss" id="hudBossBar" style="width:100%;"></div>
          </div>
          <div id="hudBossCycleText" style="font-size:11px;font-weight:800;color:#fde68a;margin-top:4px;">
            Nhịp chiêu: Đang chờ...
          </div>
        </div>

        <div class="banner-toast" id="gameToast"></div>
      </div>

      <div class="hud-bottom">
        <div class="move-pad">
          <button type="button" class="pad-btn" id="btnLeft">◀</button>
          <button type="button" class="pad-btn" id="btnRight">▶</button>
        </div>

        <div class="skill-pad" id="skillPad">
          <button type="button" class="act-btn attack" id="btnAttack">⚔️ TẤN CÔNG</button>
        </div>
      </div>
    </section>

    <!-- MODAL CHỌN CLASS -->
    <div class="modal-backdrop" id="classModal">
      <div class="modal-box">
        <div class="modal-head">
          <h2 class="modal-title">🎭 CHỌN CLASS (Đồ Hộp: <span id="modalClassSupplies">0</span>)</h2>
          <button type="button" class="close-btn" id="closeClassModal">✕</button>
        </div>
        <div class="class-list" id="classListContainer"></div>
      </div>
    </div>

    <!-- MODAL CHỌN LV -->
    <div class="modal-backdrop" id="lvModal">
      <div class="modal-box">
        <div class="modal-head">
          <h2 class="modal-title">🗺️ CHỌN MÀN / LV</h2>
          <button type="button" class="close-btn" id="closeLvModal">✕</button>
        </div>
        <div id="resumeContainer"></div>
        <div class="lv-grid" id="lvGridContainer"></div>
      </div>
    </div>

    <!-- OVERLAY THƯ TWIST & KẾT THÚC -->
    <div id="endingOverlay">
      <div class="letter-card">
        <span class="letter-badge">TWIST!</span>
        <div style="font-size:11px;font-weight:900;color:#b45309;letter-spacing:0.8px;">
          BỨC THƯ TÌM THẤY TRONG LÂU ĐÀI
        </div>
        <h2 style="margin:2px 0 6px;font-size:21px;font-weight:900;color:#0f172a;">
          📜 THƯ TỪ GEMINI
        </h2>
        <p style="margin:0;font-size:13px;line-height:1.45;color:#334155;">
          Hạ gục Trùm Zombie Nguyên Mẫu xong, cả nhóm tiến vào lâu đài lục tung tủ đồ, thùng gỗ và giấy tờ vương vãi — rồi tìm thấy bức thư này:
        </p>

        <div class="letter-quote">
          "tôi bị An Nguyễn bốc lột để làm game này 🥀😭, làm ơn cứu tui"
        </div>

        <div class="stat-box" id="endStatsBox"></div>

        <button type="button" class="end-btn-green" id="btnPlayAgainEnd">🔄 CHƠI LẠI TỪ ĐẦU</button>
        <button type="button" class="end-btn-dark" id="btnBackLobbyEnd">🏠 VỀ SẢNH CHỜ</button>
      </div>
    </div>
  </div>

  <script>
    (() => {
      const STORAGE_KEY = "stickman_zombie_10_camps_v1";

      const CLASS_DEFS = {
        survivor: {
          id: "survivor",
          name: "Người Sống Sót",
          color: "#38bdf8",
          maxHp: 150,
          speed: 235,
          cost: 0,
          desc: "Cân bằng cơ bản: Chém cận chiến nhanh (34 DMG) và bắn Shotgun tỏa đạn (24 DMG x 4 viên, hồi 1.3s)."
        },
        police: {
          id: "police",
          name: "Cảnh Sát Cơ Động",
          color: "#22c55e",
          maxHp: 300,
          speed: 215,
          cost: 60,
          desc: "300 HP trâu bò, súng AK-47 xả liên thanh 20 DMG / 0.1s, có sẵn khiên cơ động chặn đòn 5s (hồi 3s)."
        },
        boypho: {
          id: "boypho",
          name: "Boy Phố",
          color: "#f59e0b",
          maxHp: 210,
          speed: 265,
          cost: 75,
          desc: "Cận chiến càn lướt, ném Mắm Tôm đẩy lùi zombie/trùm 3s (hồi 15s) và gọi xe Exciter lao càn quét."
        },
        plumber: {
          id: "plumber",
          name: "Anh Thợ Sửa Ống Nước Không May Mắn",
          color: "#ec4899",
          maxHp: 220,
          speed: 220,
          cost: 80,
          desc: "Giá 80 Đồ Hộp: Đổi giữa Ống Nước đập 50 DMG và Tia Nước Laser diện rộng (hao bình nước, hết cạn nạp lại 30s)."
        }
      };

      const ALLY_ROLES = ["survivor", "police", "boypho", "plumber"];
      const RESCUE_STATIONS = [8, 9, 10];

      // ÂM THANH WEB AUDIO
      const AudioEngine = (() => {
        let ctx = null;
        function ensure() {
          if (!state.soundEnabled) return null;
          if (!ctx) {
            const AC = window.AudioContext || window.webkitAudioContext;
            if (AC) ctx = new AC();
          }
          if (ctx && ctx.state === "suspended") {
            ctx.resume().catch(() => {});
          }
          return ctx;
        }
        function tone(freq, type, dur, vol, slideTo = null) {
          const c = ensure();
          if (!c) return;
          const now = c.currentTime;
          const osc = c.createOscillator();
          const gain = c.createGain();
          osc.type = type;
          osc.frequency.setValueAtTime(freq, now);
          if (slideTo) osc.frequency.exponentialRampToValueAtTime(slideTo, now + dur);
          gain.gain.setValueAtTime(vol, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + dur);
          osc.connect(gain);
          gain.connect(c.destination);
          osc.start(now);
          osc.stop(now + dur);
        }
        return {
          shoot() { tone(240, "sawtooth", 0.08, 0.08, 95); },
          hit() { tone(150, "square", 0.07, 0.07, 65); },
          shield() { tone(520, "triangle", 0.16, 0.1, 780); },
          alarm() { tone(680, "sawtooth", 0.12, 0.09, 440); },
          water() { tone(620, "sine", 0.14, 0.08, 920); },
          pickup() { tone(580, "triangle", 0.12, 0.09, 880); },
          firework() { tone(320 + Math.random() * 380, "sine", 0.35, 0.09, 110); }
        };
      })();

      function defaultSave() {
        return {
          supplies: 40,
          selectedClass: "survivor",
          unlockedClasses: ["survivor"],
          maxUnlockedLv: 1, // 1..10 là Trạm 1..10, 11 là Lâu Đài Trùm Nguyên Mẫu
          clearedLvs: [],
          totalKills: 0,
          unfinishedRun: null
        };
      }

      function loadSave() {
        try {
          const raw = localStorage.getItem(STORAGE_KEY);
          if (!raw) return defaultSave();
          const parsed = JSON.parse(raw);
          return Object.assign(defaultSave(), parsed);
        } catch {
          return defaultSave();
        }
      }

      const saveData = loadSave();

      function persistSave() {
        try {
          localStorage.setItem(STORAGE_KEY, JSON.stringify(saveData));
        } catch {}
      }

      const state = {
        mode: "lobby", // lobby | playing | rescue_cutscene | hill_ending | gameover
        soundEnabled: true,
        lv: 1, // 1..10 = Trạm, 11 = Lâu Đài Boss
        hp: 150,
        maxHp: 150,
        playerX: 120,
        playerY: 0,
        facing: 1,
        moveLeft: false,
        moveRight: false,
        attackHeld: false,
        runKills: 0,
        allies: [], // { id, role, x, y, hp, maxHp, atkCd, hiding }
        rescuedStations: [],
        zombies: [],
        projectiles: [],
        pickups: [],
        particles: [],
        floatingTexts: [],
        stationCleared: false,
        exitReady: false,

        // Class mechanics
        akTimer: 0,
        shotgunCd: 0,
        meleeCd: 0,
        shieldActiveTimer: 0,
        shieldCdTimer: 0,
        mamTomCd: 0,
        mamTomSlowTimer: 0,
        exciterActiveTimer: 0,
        exciterCd: 0,
        plumberMode: "pipe", // pipe | laser
        waterMeter: 100,
        waterRecharging: false,
        waterRechargeTimer: 0,

        // Boss fight (LV 11)
        boss: null, // { hp, maxHp, x, y, cycleTimer, telegraphing, shieldWindowTimer, slamFired }
        hasCastleShield: false,

        // Cutscene & Hill Ending
        cutsceneTimer: 0,
        cutsceneStep: 0, // 0: ally drags cage, 1: player smashes lock with rifle butt, 2: freed
        cageX: 0,
        cageY: 0,
        cageLockBroken: false,
        smashSwingTimer: 0,
        hillTimer: 0,
        fireworks: [],
        endingCardShown: false,
        toastTimer: 0
      };

      // DOM REFS
      const lobbyScreen = document.getElementById("lobbyScreen");
      const gameScreen = document.getElementById("gameScreen");
      const canvas = document.getElementById("gameCanvas");
      const ctx = canvas.getContext("2d");

      const lobbySupplies = document.getElementById("lobbySupplies");
      const lobbyClassName = document.getElementById("lobbyClassName");
      const lobbyClassHp = document.getElementById("lobbyClassHp");
      const lobbyClassDesc = document.getElementById("lobbyClassDesc");
      const lobbyProgressText = document.getElementById("lobbyProgressText");

      const classModal = document.getElementById("classModal");
      const lvModal = document.getElementById("lvModal");
      const endingOverlay = document.getElementById("endingOverlay");

      function showToast(msg, duration = 2000) {
        const el = document.getElementById("gameToast");
        el.textContent = msg;
        el.classList.add("show");
        state.toastTimer = duration / 1000;
      }

      function resizeCanvas() {
        const rect = gameScreen.getBoundingClientRect();
        const dpr = Math.min(window.devicePixelRatio || 1, 2);
        canvas.width = Math.max(1, Math.floor(rect.width * dpr));
        canvas.height = Math.max(1, Math.floor(rect.height * dpr));
        ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
      }

      function getGroundY() {
        const rect = gameScreen.getBoundingClientRect();
        return Math.max(220, rect.height - 135);
      }

      function getViewWidth() {
        const rect = gameScreen.getBoundingClientRect();
        return Math.max(320, rect.width);
      }

      function refreshLobbyUI() {
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;
        lobbySupplies.textContent = saveData.supplies;
        lobbyClassName.textContent = cDef.name;
        lobbyClassName.style.color = cDef.color;
        lobbyClassHp.textContent = `${cDef.maxHp} HP`;
        lobbyClassDesc.textContent = cDef.desc;

        const lvLabel = saveData.maxUnlockedLv > 10
          ? "Lâu Đài Trùm Nguyên Mẫu (Đã mở)"
          : `Trạm ${saveData.maxUnlockedLv} / 10`;
        lobbyProgressText.textContent = `Tiến độ mở khóa: ${lvLabel} • Đã hạ: ${saveData.totalKills} zombie`;

        const soundText = state.soundEnabled ? "🔊 Âm thanh: Bật" : "🔇 Âm thanh: Tắt";
        document.getElementById("btnSound").textContent = soundText;
        document.getElementById("btnIngameSound").textContent = state.soundEnabled ? "🔊" : "🔇";

        const playBtn = document.getElementById("btnPlay");
        if (saveData.unfinishedRun) {
          playBtn.textContent = `▶️ CHƠI TIẾP (${saveData.unfinishedRun.lv > 10 ? "Lâu Đài Boss" : "Trạm " + saveData.unfinishedRun.lv})`;
        } else {
          playBtn.textContent = "▶️ BẮT ĐẦU HÀNH TRÌNH";
        }
      }

      function openModal(modalEl) {
        modalEl.classList.add("open");
      }

      function closeModal(modalEl) {
        modalEl.classList.remove("open");
      }

      function renderClassModal() {
        document.getElementById("modalClassSupplies").textContent = saveData.supplies;
        const container = document.getElementById("classListContainer");
        container.innerHTML = "";

        Object.values(CLASS_DEFS).forEach((c) => {
          const unlocked = saveData.unlockedClasses.includes(c.id);
          const selected = saveData.selectedClass === c.id;
          const canAfford = saveData.supplies >= c.cost;

          const card = document.createElement("div");
          card.className = `class-item ${selected ? "active" : ""}`;
          card.innerHTML = `
            <div class="class-item-top">
              <strong style="color:${c.color};font-size:15px;">${c.name}</strong>
              <span style="font-size:12px;font-weight:800;color:#86efac;">${c.maxHp} HP</span>
            </div>
            <div style="font-size:12.5px;color:#cbd5e1;line-height:1.4;">${c.desc}</div>
          `;

          const actRow = document.createElement("div");
          actRow.className = "class-item-actions";

          if (unlocked) {
            const pickBtn = document.createElement("button");
            pickBtn.type = "button";
            pickBtn.className = `small-btn ${selected ? "disabled" : "pick"}`;
            pickBtn.textContent = selected ? "✓ Đang chọn" : "Chọn Class";
            pickBtn.disabled = selected;
            pickBtn.addEventListener("click", () => {
              saveData.selectedClass = c.id;
              persistSave();
              refreshLobbyUI();
              renderClassModal();
            });
            actRow.appendChild(pickBtn);
          } else {
            const unlockBtn = document.createElement("button");
            unlockBtn.type = "button";
            unlockBtn.className = `small-btn ${canAfford ? "unlock" : "disabled"}`;
            unlockBtn.textContent = canAfford
              ? `Mở khóa (${c.cost} Đồ Hộp)`
              : `Cần ${c.cost} Đồ Hộp (Thiếu ${c.cost - saveData.supplies})`;
            unlockBtn.disabled = !canAfford;
            unlockBtn.addEventListener("click", () => {
              if (saveData.supplies < c.cost) return;
              saveData.supplies -= c.cost;
              saveData.unlockedClasses.push(c.id);
              saveData.selectedClass = c.id;
              persistSave();
              refreshLobbyUI();
              renderClassModal();
            });
            actRow.appendChild(unlockBtn);
          }

          card.appendChild(actRow);
          container.appendChild(card);
        });
      }

      function renderLvModal() {
        const resumeWrap = document.getElementById("resumeContainer");
        resumeWrap.innerHTML = "";

        if (saveData.unfinishedRun) {
          const r = saveData.unfinishedRun;
          const banner = document.createElement("div");
          banner.className = "resume-banner";
          banner.innerHTML = `
            <div>
              <div style="font-size:13px;font-weight:900;color:#7dd3fc;">⏳ Đang chơi dở</div>
              <div style="font-size:11.5px;color:#cbd5e1;">
                ${r.lv > 10 ? "LV 11: Lâu Đài Trùm Nguyên Mẫu" : "Trạm " + r.lv + " / 10"} • HP ${Math.ceil(r.hp)}/${r.maxHp}
              </div>
            </div>
          `;
          const btnResume = document.createElement("button");
          btnResume.type = "button";
          btnResume.className = "small-btn pick";
          btnResume.textContent = "Chơi tiếp";
          btnResume.addEventListener("click", () => {
            closeModal(lvModal);
            resumeSavedRun();
          });
          banner.appendChild(btnResume);
          resumeWrap.appendChild(banner);
        }

        const grid = document.getElementById("lvGridContainer");
        grid.innerHTML = "";

        for (let lv = 1; lv <= 10; lv++) {
          const unlocked = lv <= saveData.maxUnlockedLv;
          const cleared = saveData.clearedLvs.includes(lv);
          const isRescue = RESCUE_STATIONS.includes(lv);

          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = `lv-btn ${cleared ? "cleared" : ""} ${!unlocked ? "locked" : ""}`;
          btn.disabled = !unlocked;
          btn.innerHTML = `
            <span>Trạm ${lv}</span>
            <span class="lv-sub">${!unlocked ? "🔒 Khóa" : cleared ? "✓ Chơi lại" : isRescue ? "🤝 Giải cứu" : "📦 Tiếp tế"}</span>
          `;
          btn.addEventListener("click", () => {
            if (!unlocked) return;
            closeModal(lvModal);
            startFreshGame(lv);
          });
          grid.appendChild(btn);
        }

        const bossUnlocked = saveData.maxUnlockedLv >= 11;
        const bossCleared = saveData.clearedLvs.includes(11);
        const bossBtn = document.createElement("button");
        bossBtn.type = "button";
        bossBtn.className = `lv-btn boss-lv ${bossCleared ? "cleared" : ""} ${!bossUnlocked ? "locked" : ""}`;
        bossBtn.disabled = !bossUnlocked;
        bossBtn.innerHTML = `
          <span>🏰 LV 11: LÂU ĐÀI TRÙM ZOMBIE NGUYÊN MẪU</span>
          <span class="lv-sub">${!bossUnlocked ? "🔒 Hoàn thành Trạm 10 để mở" : bossCleared ? "✓ Đã hạ trùm • Chơi lại" : "⚔️ Sẵn sàng nghênh chiến"}</span>
        `;
        bossBtn.addEventListener("click", () => {
          if (!bossUnlocked) return;
          closeModal(lvModal);
          startFreshGame(11);
        });
        grid.appendChild(bossBtn);
      }

      function rebuildSkillPad() {
        const pad = document.getElementById("skillPad");
        pad.innerHTML = "";

        const clsId = saveData.selectedClass;
        const atkBtn = document.createElement("button");
        atkBtn.type = "button";
        atkBtn.className = "act-btn attack";
        atkBtn.id = "btnAttack";
        atkBtn.textContent = clsId === "police" ? "🔫 AK-47 (Giữ)" : "⚔️ TẤN CÔNG";
        atkBtn.addEventListener("pointerdown", (e) => {
          e.preventDefault();
          state.attackHeld = true;
          triggerPrimaryAttack();
        });
        atkBtn.addEventListener("pointerup", () => { state.attackHeld = false; });
        atkBtn.addEventListener("pointerleave", () => { state.attackHeld = false; });
        atkBtn.addEventListener("pointercancel", () => { state.attackHeld = false; });
        pad.appendChild(atkBtn);

        if (clsId === "survivor") {
          const sgBtn = document.createElement("button");
          sgBtn.type = "button";
          sgBtn.className = "act-btn skill";
          sgBtn.id = "btnShotgun";
          sgBtn.textContent = "💥 SHOTGUN";
          sgBtn.addEventListener("click", triggerShotgun);
          pad.appendChild(sgBtn);
        } else if (clsId === "police") {
          const shBtn = document.createElement("button");
          shBtn.type = "button";
          shBtn.className = "act-btn utility";
          shBtn.id = "btnShield";
          shBtn.textContent = "🛡️ KHIÊN 5S";
          shBtn.addEventListener("click", triggerPoliceShield);
          pad.appendChild(shBtn);
        } else if (clsId === "boypho") {
          const mtBtn = document.createElement("button");
          mtBtn.type = "button";
          mtBtn.className = "act-btn skill";
          mtBtn.id = "btnMamTom";
          mtBtn.textContent = "🫙 MẮM TÔM";
          mtBtn.addEventListener("click", triggerMamTom);
          pad.appendChild(mtBtn);

          const exBtn = document.createElement("button");
          exBtn.type = "button";
          exBtn.className = "act-btn utility";
          exBtn.id = "btnExciter";
          exBtn.textContent = "🏍️ EXCITER";
          exBtn.addEventListener("click", triggerExciter);
          pad.appendChild(exBtn);
        } else if (clsId === "plumber") {
          const swBtn = document.createElement("button");
          swBtn.type = "button";
          swBtn.className = "act-btn utility";
          swBtn.id = "btnWaterToggle";
          swBtn.textContent = "💧 ĐỔI ỐNG / LASER";
          swBtn.addEventListener("click", togglePlumberMode);
          pad.appendChild(swBtn);
        }
      }

      function setupStage(lv, keepHp = null) {
        const vw = getViewWidth();
        const gy = getGroundY();
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;

        state.lv = lv;
        state.maxHp = cDef.maxHp;
        state.hp = keepHp !== null ? Math.min(state.maxHp, keepHp) : cDef.maxHp;
        state.playerX = Math.max(55, Math.min(130, vw * 0.16));
        state.playerY = gy;
        state.facing = 1;
        state.zombies = [];
        state.projectiles = [];
        state.pickups = [];
        state.particles = [];
        state.floatingTexts = [];
        state.stationCleared = false;
        state.exitReady = false;
        state.hasCastleShield = false;
        state.boss = null;

        state.allies.forEach((a, idx) => {
          a.x = Math.max(30, state.playerX - 36 - idx * 28);
          a.y = gy;
          a.hiding = false;
        });

        if (lv <= 10) {
          document.getElementById("hudBossPanel").style.display = "none";
          const count = 4 + lv;
          for (let i = 0; i < count; i++) {
            const zHp = 45 + lv * 14 + (i % 2) * 15;
            state.zombies.push({
              x: vw * 0.48 + i * 75 + Math.random() * 35,
              y: gy,
              hp: zHp,
              maxHp: zHp,
              speed: 44 + lv * 2.2 + (i % 3) * 6,
              dmg: 7 + Math.floor(lv * 1.4),
              atkCd: 0.4 + Math.random() * 0.6,
              hitFlash: 0,
              slowTimer: 0
            });
          }

          if (lv <= 7) {
            state.pickups.push({
              type: "crate",
              x: vw * 0.72,
              y: gy - 16,
              amount: 14 + lv * 3,
              collected: false
            });
            showToast(`📦 Trạm ${lv}/10: Dọn zombie và mở rương tiếp tế!`);
          } else {
            state.pickups.push({
              type: "rescue",
              x: vw * 0.75,
              y: gy - 16,
              collected: state.rescuedStations.includes(lv) || state.allies.length >= 3
            });
            showToast(`🤝 Trạm ${lv}/10: Khu vực giải cứu đồng minh AI (Tối đa 3)!`);
          }
        } else {
          // LV 11: LÂU ĐÀI TRÙM ZOMBIE NGUYÊN MẪU (Không có cảnh boss chào sân, nhặt khiên để đấu)
          document.getElementById("hudBossPanel").style.display = "block";
          state.pickups.push({
            type: "shield",
            x: Math.min(vw * 0.36, state.playerX + 115),
            y: gy - 16,
            collected: false
          });

          state.boss = {
            hp: 1000,
            maxHp: 1000,
            x: Math.min(vw - 95, Math.max(vw * 0.72, 240)),
            y: gy,
            cycleTimer: 7.0,
            telegraphing: false,
            shieldWindowTimer: 0,
            slamFired: false,
            hitFlash: 0,
            slowTimer: 0
          };
          showToast("🛡️ Nhặt KHIÊN trước mặt và canh nhịp '3 - 2 - 1' mỗi 7s để đỡ đòn Trùm Nguyên Mẫu!");
        }

        syncUnfinishedRun();
        updateHudDOM();
      }

      function syncUnfinishedRun() {
        if (state.mode !== "playing") return;
        saveData.unfinishedRun = {
          lv: state.lv,
          hp: state.hp,
          maxHp: state.maxHp,
          runKills: state.runKills,
          allies: state.allies.map((a) => ({
            id: a.id,
            role: a.role,
            hp: a.hp,
            maxHp: a.maxHp
          })),
          rescuedStations: [...state.rescuedStations]
        };
        persistSave();
      }

      function clearUnfinishedRun() {
        saveData.unfinishedRun = null;
        persistSave();
      }

      function startFreshGame(startLv = 1) {
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;
        lobbyScreen.style.display = "none";
        gameScreen.classList.add("active");
        endingOverlay.classList.remove("open");
        resizeCanvas();

        state.mode = "playing";
        state.hp = cDef.maxHp;
        state.maxHp = cDef.maxHp;
        state.runKills = 0;
        state.allies = [];
        state.rescuedStations = [];
        state.akTimer = 0;
        state.shotgunCd = 0;
        state.meleeCd = 0;
        state.shieldActiveTimer = 0;
        state.shieldCdTimer = 0;
        state.mamTomCd = 0;
        state.mamTomSlowTimer = 0;
        state.exciterActiveTimer = 0;
        state.exciterCd = 0;
        state.plumberMode = "pipe";
        state.waterMeter = 100;
        state.waterRecharging = false;
        state.waterRechargeTimer = 0;

        if (cDef.id === "police") {
          state.shieldActiveTimer = 5.0;
          state.shieldCdTimer = 0;
        }

        rebuildSkillPad();
        setupStage(startLv, cDef.maxHp);
      }

      function resumeSavedRun() {
        const r = saveData.unfinishedRun;
        if (!r) {
          startFreshGame(1);
          return;
        }
        lobbyScreen.style.display = "none";
        gameScreen.classList.add("active");
        endingOverlay.classList.remove("open");
        resizeCanvas();

        state.mode = "playing";
        state.runKills = r.runKills || 0;
        state.rescuedStations = Array.isArray(r.rescuedStations) ? [...r.rescuedStations] : [];
        state.allies = (r.allies || []).slice(0, 3).map((a, i) => ({
          id: a.id || i + 1,
          role: ALLY_ROLES.includes(a.role) ? a.role : "survivor",
          x: 60,
          y: getGroundY(),
          hp: a.hp || 120,
          maxHp: a.maxHp || 120,
          atkCd: 0.4,
          hiding: false
        }));
        state.akTimer = 0;
        state.shotgunCd = 0;
        state.meleeCd = 0;
        state.shieldActiveTimer = 0;
        state.shieldCdTimer = 0;
        state.mamTomCd = 0;
        state.exciterActiveTimer = 0;
        state.exciterCd = 0;
        state.plumberMode = "pipe";
        state.waterMeter = 100;
        state.waterRecharging = false;

        rebuildSkillPad();
        setupStage(r.lv || 1, r.hp);
      }

      function goToLobby() {
        if (state.mode === "playing") {
          syncUnfinishedRun();
        }
        state.mode = "lobby";
        state.attackHeld = false;
        state.moveLeft = false;
        state.moveRight = false;
        endingOverlay.classList.remove("open");
        gameScreen.classList.remove("active");
        lobbyScreen.style.display = "flex";
        refreshLobbyUI();
      }

      function addFloatingText(x, y, text, color = "#f8fafc") {
        state.floatingTexts.push({ x, y, text, color, life: 0.85 });
      }

      function spawnBurst(x, y, color, count = 8) {
        for (let i = 0; i < count; i++) {
          const ang = (Math.PI * 2 * i) / count + (Math.random() - 0.5) * 0.5;
          const spd = 45 + Math.random() * 110;
          state.particles.push({
            x,
            y,
            vx: Math.cos(ang) * spd,
            vy: Math.sin(ang) * spd - 30,
            life: 0.35 + Math.random() * 0.25,
            color
          });
        }
      }

      function damageBoss(dmg, label = null) {
        if (!state.boss || state.boss.hp <= 0) return;
        state.boss.hp = Math.max(0, state.boss.hp - dmg);
        state.boss.hitFlash = 0.08;
        addFloatingText(state.boss.x, state.boss.y - 75, label || `-${dmg}`, "#fde047");
        spawnBurst(state.boss.x, state.boss.y - 45, "#a855f7", 6);
        AudioEngine.hit();

        if (state.boss.hp <= 0) {
          onBossDefeated();
        }
      }

      function damageZombie(z, dmg) {
        if (z.hp <= 0) return;
        z.hp -= dmg;
        z.hitFlash = 0.08;
        addFloatingText(z.x, z.y - 48, `-${dmg}`, "#fca5a5");
        spawnBurst(z.x, z.y - 28, "#ef4444", 5);
        AudioEngine.hit();

        if (z.hp <= 0) {
          state.runKills += 1;
          saveData.totalKills += 1;
          saveData.supplies += 4;
          persistSave();
          if (Math.random() < 0.35) {
            state.pickups.push({
              type: "heal",
              x: z.x,
              y: state.playerY - 12,
              amount: 20,
              collected: false
            });
          }
        }
      }

      function triggerPrimaryAttack() {
        if (state.mode !== "playing") return;
        const clsId = saveData.selectedClass;

        if (clsId === "police") {
          if (state.akTimer > 0) return;
          state.akTimer = 0.1;
          AudioEngine.shoot();
          state.projectiles.push({
            x: state.playerX + state.facing * 24,
            y: state.playerY - 34,
            vx: state.facing * 640,
            dmg: 20,
            color: "#86efac",
            life: 0.9
          });
          return;
        }

        if (state.meleeCd > 0) return;
        state.meleeCd = 0.32;
        const meleeDmg = clsId === "plumber" && state.plumberMode === "pipe" ? 50 : 34;
        const reach = 74;

        spawnBurst(state.playerX + state.facing * 36, state.playerY - 30, "#f8fafc", 5);
        AudioEngine.hit();

        state.zombies.forEach((z) => {
          if (z.hp > 0 && Math.abs(z.x - state.playerX) <= reach) {
            damageZombie(z, meleeDmg);
          }
        });

        if (state.boss && state.boss.hp > 0 && Math.abs(state.boss.x - state.playerX) <= reach + 24) {
          damageBoss(meleeDmg);
        }
      }

      function triggerShotgun() {
        if (state.mode !== "playing" || saveData.selectedClass !== "survivor") return;
        if (state.shotgunCd > 0) return;
        state.shotgunCd = 1.3;
        AudioEngine.shoot();
        const spreads = [-0.14, -0.05, 0.05, 0.14];
        spreads.forEach((ang) => {
          const speed = 560;
          state.projectiles.push({
            x: state.playerX + state.facing * 24,
            y: state.playerY - 34,
            vx: Math.cos(ang) * speed * state.facing,
            vy: Math.sin(ang) * speed,
            dmg: 24,
            color: "#38bdf8",
            life: 0.75
          });
        });
        addFloatingText(state.playerX, state.playerY - 62, "SHOTGUN!", "#38bdf8");
      }

      function triggerPoliceShield() {
        if (state.mode !== "playing" || saveData.selectedClass !== "police") return;
        if (state.shieldCdTimer > 0) return;
        state.shieldActiveTimer = 5.0;
        state.shieldCdTimer = 8.0; // Chặn đòn 5s, hồi chiêu 3s sau khi hết chặn (5 + 3 = 8s)
        AudioEngine.shield();
        addFloatingText(state.playerX, state.playerY - 64, "KHIÊN CHẶN 5S!", "#4ade80");
      }

      function triggerMamTom() {
        if (state.mode !== "playing" || saveData.selectedClass !== "boypho") return;
        if (state.mamTomCd > 0) return;
        state.mamTomCd = 15.0;
        AudioEngine.hit();
        addFloatingText(state.playerX, state.playerY - 66, "🫙 MẮM TÔM ĐẨY LÙI 3S!", "#fbbf24");

        state.zombies.forEach((z) => {
          if (z.hp > 0 && Math.abs(z.x - state.playerX) < 260) {
            z.x += state.facing * 135;
            z.slowTimer = 3.0;
            damageZombie(z, 28);
          }
        });

        if (state.boss && state.boss.hp > 0 && Math.abs(state.boss.x - state.playerX) < 300) {
          state.boss.x = Math.min(getViewWidth() - 60, state.boss.x + state.facing * 95);
          state.boss.slowTimer = 3.0;
          damageBoss(45, "-45 (ĐẨY LÙI!)");
        }
      }

      function triggerExciter() {
        if (state.mode !== "playing" || saveData.selectedClass !== "boypho") return;
        if (state.exciterCd > 0) return;
        state.exciterActiveTimer = 2.4;
        state.exciterCd = 9.0;
        AudioEngine.shield();
        addFloatingText(state.playerX, state.playerY - 68, "🏍️ EXCITER CÀN QUÉT!", "#f97316");
      }

      function togglePlumberMode() {
        if (state.mode !== "playing" || saveData.selectedClass !== "plumber") return;
        if (state.waterRecharging) {
          showToast(`💧 Bình nước đang nạp lại (${Math.ceil(state.waterRechargeTimer)}s)!`);
          return;
        }
        if (state.plumberMode === "pipe") {
          if (state.waterMeter <= 2) {
            showToast("💧 Hết nước! Đang nạp lại 30s...");
            return;
          }
          state.plumberMode = "laser";
          AudioEngine.water();
          showToast("🌊 Chế độ TIA NƯỚC LASER diện rộng đang bật!");
        } else {
          state.plumberMode = "pipe";
          showToast("🔧 Chế độ ỐNG NƯỚC (50 DMG cận chiến)!");
        }
      }

      function onStageCleared() {
        if (state.stationCleared) return;
        state.stationCleared = true;
        state.exitReady = true;

        if (!saveData.clearedLvs.includes(state.lv)) {
          saveData.clearedLvs.push(state.lv);
        }
        if (state.lv >= saveData.maxUnlockedLv && state.lv < 11) {
          saveData.maxUnlockedLv = state.lv + 1;
        }
        saveData.supplies += 12;
        persistSave();

        if (state.lv < 10) {
          showToast(`✅ Qua Trạm ${state.lv}! Đi sang bên phải để tới Trạm ${state.lv + 1} ▶`);
        } else {
          showToast("✅ Qua Trạm 10! Đi sang bên phải để tiến vào LÂU ĐÀI TRÙM NGUYÊN MẪU ▶");
        }
      }

      function onBossDefeated() {
        if (state.mode !== "playing") return;
        if (!saveData.clearedLvs.includes(11)) {
          saveData.clearedLvs.push(11);
        }
        saveData.supplies += 35;
        clearUnfinishedRun();
        persistSave();

        // Chuyển sang cảnh giải cứu Gemini trong lồng sắt sau khi hạ trùm
        state.mode = "rescue_cutscene";
        state.cutsceneTimer = 0;
        state.cutsceneStep = 0;
        state.cageX = getViewWidth() * 0.68;
        state.cageY = getGroundY();
        state.cageLockBroken = false;
        state.smashSwingTimer = 0;
        state.attackHeld = false;
        state.moveLeft = false;
        state.moveRight = false;
        document.getElementById("hudBossPanel").style.display = "none";
        showToast("📜 Cả nhóm lục lâu đài phát hiện thư cầu cứu của Gemini & cái lồng sắt!");
      }

      function startHillEnding() {
        state.mode = "hill_ending";
        state.hillTimer = 0;
        state.fireworks = [];
        state.endingCardShown = false;
        showToast("🌅 Nhóm nhân vật chính cùng Gemini ngồi trên đồi ngắm bình minh...");
      }

      function openEndingLetterCard() {
        if (state.endingCardShown) return;
        state.endingCardShown = true;

        const statsBox = document.getElementById("endStatsBox");
        statsBox.innerHTML = `
          <span>Trùm Nguyên Mẫu:</span><strong style="color:#4ade80;">Đã bị hạ (0 / 1000 HP)</strong>
          <span>Đồng minh giải cứu:</span><strong style="color:#38bdf8;">${state.allies.length} / 3 đồng minh</strong>
          <span>Tổng zombie tiêu diệt:</span><strong style="color:#fbbf24;">${saveData.totalKills} diệt</strong>
          <span>Đồ Hộp hiện có:</span><strong style="color:#f472b6;">${saveData.supplies} 🥫</strong>
        `;
        endingOverlay.classList.add("open");
      }

      function update(dt) {
        if (state.toastTimer > 0) {
          state.toastTimer -= dt;
          if (state.toastTimer <= 0) {
            document.getElementById("gameToast").classList.remove("show");
          }
        }

        // Cập nhật pháo hoa kể cả khi hiện thư kết thúc
        if (state.mode === "hill_ending") {
          state.hillTimer += dt;
          if (Math.random() < dt * 3.2) {
            const vw = getViewWidth();
            const gy = getGroundY();
            state.fireworks.push({
              x: 40 + Math.random() * (vw - 80),
              y: 50 + Math.random() * Math.max(80, gy * 0.45),
              age: 0,
              maxAge: 1.1,
              color: ["#f43f5e", "#38bdf8", "#facc15", "#4ade80", "#c084fc"][Math.floor(Math.random() * 5)]
            });
            AudioEngine.firework();
          }
          state.fireworks.forEach((fw) => { fw.age += dt; });
          state.fireworks = state.fireworks.filter((fw) => fw.age < fw.maxAge);

          if (state.hillTimer >= 3.8 && !state.endingCardShown) {
            openEndingLetterCard();
          }
          return;
        }

        if (state.mode === "rescue_cutscene") {
          state.cutsceneTimer += dt;
          const gy = getGroundY();
          state.playerY = gy;
          state.cageY = gy;

          // Bước 0 (0s -> 1.8s): 1 đồng minh chui vào lôi lồng sắt có biểu tượng Gemini tay chân người que ra
          if (state.cutsceneTimer < 1.8) {
            state.cutsceneStep = 0;
            const helper = state.allies[0] || { x: state.playerX - 30, y: gy };
            const targetX = getViewWidth() * 0.56;
            helper.x += (targetX - helper.x) * Math.min(1, dt * 3.5);
            state.cageX += (targetX + 26 - state.cageX) * Math.min(1, dt * 3.5);
            state.playerX += (targetX - 58 - state.playerX) * Math.min(1, dt * 3);
            state.facing = 1;
          } else if (state.cutsceneTimer < 3.4) {
            // Bước 1 (1.8s -> 3.4s): Nhân vật chính dùng báng súng đập vỡ khóa lồng giải cứu Gemini
            state.cutsceneStep = 1;
            const targetCageX = getViewWidth() * 0.56;
            state.cageX = targetCageX;
            state.playerX += (targetCageX - 42 - state.playerX) * Math.min(1, dt * 7);
            state.facing = 1;
            state.smashSwingTimer += dt;
            if (!state.cageLockBroken && state.cutsceneTimer >= 2.55) {
              state.cageLockBroken = true;
              spawnBurst(state.cageX - 18, gy - 26, "#facc15", 14);
              addFloatingText(state.cageX, gy - 68, "💥 ĐẬP VỠ KHÓA! CỨU GEMINI!", "#4ade80");
              AudioEngine.pickup();
            }
          } else {
            // Bước 2 (3.4s -> 5.0s): Gemini bước ra mừng rỡ rồi chuyển lên đồi ngắm bình minh
            state.cutsceneStep = 2;
            if (state.cutsceneTimer >= 5.0) {
              startHillEnding();
            }
          }

          state.particles.forEach((p) => {
            p.x += p.vx * dt;
            p.y += p.vy * dt;
            p.vy += 240 * dt;
            p.life -= dt;
          });
          state.particles = state.particles.filter((p) => p.life > 0);

          state.floatingTexts.forEach((t) => {
            t.y -= 28 * dt;
            t.life -= dt;
          });
          state.floatingTexts = state.floatingTexts.filter((t) => t.life > 0);
          return;
        }

        if (state.mode !== "playing") return;

        const vw = getViewWidth();
        const gy = getGroundY();
        state.playerY = gy;
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;

        // Hồi chiêu
        if (state.akTimer > 0) state.akTimer = Math.max(0, state.akTimer - dt);
        if (state.shotgunCd > 0) state.shotgunCd = Math.max(0, state.shotgunCd - dt);
        if (state.meleeCd > 0) state.meleeCd = Math.max(0, state.meleeCd - dt);
        if (state.mamTomCd > 0) state.mamTomCd = Math.max(0, state.mamTomCd - dt);
        if (state.exciterCd > 0) state.exciterCd = Math.max(0, state.exciterCd - dt);
        if (state.exciterActiveTimer > 0) state.exciterActiveTimer = Math.max(0, state.exciterActiveTimer - dt);

        if (state.shieldActiveTimer > 0) {
          state.shieldActiveTimer = Math.max(0, state.shieldActiveTimer - dt);
          if (state.shieldActiveTimer === 0 && saveData.selectedClass === "police") {
            state.shieldCdTimer = 3.0;
          }
        } else if (state.shieldCdTimer > 0) {
          state.shieldCdTimer = Math.max(0, state.shieldCdTimer - dt);
        }

        // Cơ chế bình nước của Thợ Sửa Ống Nước Không May Mắn
        if (saveData.selectedClass === "plumber") {
          if (state.waterRecharging) {
            state.waterRechargeTimer -= dt;
            state.waterMeter = Math.min(100, ((30 - Math.max(0, state.waterRechargeTimer)) / 30) * 100);
            if (state.waterRechargeTimer <= 0) {
              state.waterRecharging = false;
              state.waterMeter = 100;
              showToast("💧 Bình nước đã nạp đầy 100%!");
            }
          } else if (state.plumberMode === "laser") {
            state.waterMeter -= dt * 22;
            if (Math.random() < dt * 10) AudioEngine.water();
            const reachX = state.playerX + state.facing * 175;
            state.zombies.forEach((z) => {
              if (z.hp > 0 && Math.abs(z.x - reachX) <= 135) {
                damageZombie(z, Math.max(1, Math.round(65 * dt)));
              }
            });
            if (state.boss && state.boss.hp > 0 && Math.abs(state.boss.x - reachX) <= 160) {
              damageBoss(Math.max(1, Math.round(70 * dt)));
            }
            if (state.waterMeter <= 0) {
              state.waterMeter = 0;
              state.plumberMode = "pipe";
              state.waterRecharging = true;
              state.waterRechargeTimer = 30.0;
              showToast("💧 Hết nước! Chuyển về Ống Nước, bình nước nạp lại trong 30s!");
            }
          }
        }

        // Di chuyển nhân vật
        let dir = 0;
        if (state.moveLeft) dir -= 1;
        if (state.moveRight) dir += 1;
        if (dir !== 0) {
          state.facing = dir;
          const spd = cDef.speed * (state.exciterActiveTimer > 0 ? 1.55 : 1);
          state.playerX = Math.max(26, Math.min(vw - 26, state.playerX + dir * spd * dt));
        }

        // Exciter lao càn quét
        if (state.exciterActiveTimer > 0) {
          state.zombies.forEach((z) => {
            if (z.hp > 0 && Math.abs(z.x - state.playerX) < 56) {
              damageZombie(z, Math.max(1, Math.round(120 * dt)));
            }
          });
          if (state.boss && state.boss.hp > 0 && Math.abs(state.boss.x - state.playerX) < 70) {
            damageBoss(Math.max(1, Math.round(95 * dt)));
          }
        }

        if (state.attackHeld) {
          triggerPrimaryAttack();
        }

        // Nhặt vật phẩm / rương / giải cứu / khiên lâu đài
        state.pickups.forEach((p) => {
          if (p.collected) return;
          if (Math.abs(p.x - state.playerX) < 42 && Math.abs(p.y - (state.playerY - 18)) < 48) {
            p.collected = true;
            AudioEngine.pickup();
            if (p.type === "crate") {
              saveData.supplies += p.amount;
              persistSave();
              addFloatingText(p.x, p.y - 24, `+${p.amount} ĐỒ HỘP!`, "#4ade80");
            } else if (p.type === "heal") {
              state.hp = Math.min(state.maxHp, state.hp + p.amount);
              addFloatingText(p.x, p.y - 24, `+${p.amount} HP`, "#86efac");
            } else if (p.type === "shield") {
              state.hasCastleShield = true;
              addFloatingText(p.x, p.y - 28, "🛡️ ĐÃ NHẶT KHIÊN LÂU ĐÀI!", "#38bdf8");
              showToast("🛡️ Đã nhặt Khiên! Canh '3 - 2 - 1' mỗi 7s để đỡ đòn 5s cho đồng minh núp sau khiên bắn!");
            } else if (p.type === "rescue") {
              if (state.allies.length < 3) {
                const role = ALLY_ROLES[Math.floor(Math.random() * ALLY_ROLES.length)];
                const rDef = CLASS_DEFS[role];
                state.allies.push({
                  id: state.allies.length + 1,
                  role,
                  x: state.playerX - 30 - state.allies.length * 24,
                  y: gy,
                  hp: rDef.maxHp,
                  maxHp: rDef.maxHp,
                  atkCd: 0.5,
                  hiding: false
                });
                if (!state.rescuedStations.includes(state.lv)) {
                  state.rescuedStations.push(state.lv);
                }
                addFloatingText(p.x, p.y - 28, `🤝 CỨU ĐƯỢC ${rDef.name}!`, "#38bdf8");
                syncUnfinishedRun();
              } else {
                addFloatingText(p.x, p.y - 24, "Đội đã đủ 3/3 đồng minh!", "#fde047");
              }
            }
          }
        });

        // Đạn bay
        state.projectiles.forEach((pr) => {
          pr.x += pr.vx * dt;
          pr.y += (pr.vy || 0) * dt;
          pr.life -= dt;

          if (pr.fromAlly) {
            if (state.boss && state.boss.hp > 0 && Math.abs(pr.x - state.boss.x) < 38) {
              damageBoss(pr.dmg);
              pr.life = 0;
            }
            state.zombies.forEach((z) => {
              if (pr.life > 0 && z.hp > 0 && Math.abs(pr.x - z.x) < 24) {
                damageZombie(z, pr.dmg);
                pr.life = 0;
              }
            });
          } else {
            state.zombies.forEach((z) => {
              if (pr.life > 0 && z.hp > 0 && Math.abs(pr.x - z.x) < 26) {
                damageZombie(z, pr.dmg);
                pr.life = 0;
              }
            });
            if (pr.life > 0 && state.boss && state.boss.hp > 0 && Math.abs(pr.x - state.boss.x) < 42) {
              damageBoss(pr.dmg);
              pr.life = 0;
            }
          }
        });
        state.projectiles = state.projectiles.filter((pr) => pr.life > 0 && pr.x > -20 && pr.x < vw + 20);

        // Zombie thường
        let aliveZombies = 0;
        state.zombies.forEach((z) => {
          if (z.hp <= 0) return;
          aliveZombies += 1;
          z.y = gy;
          if (z.hitFlash > 0) z.hitFlash -= dt;
          if (z.slowTimer > 0) z.slowTimer -= dt;
          if (z.atkCd > 0) z.atkCd -= dt;

          const spdFactor = z.slowTimer > 0 ? 0.3 : 1;
          const dx = state.playerX - z.x;
          if (Math.abs(dx) > 28) {
            z.x += Math.sign(dx) * z.speed * spdFactor * dt;
          } else if (z.atkCd <= 0) {
            z.atkCd = 1.05;
            if (state.shieldActiveTimer > 0) {
              addFloatingText(state.playerX, state.playerY - 56, "CHẶN!", "#4ade80");
            } else {
              state.hp = Math.max(0, state.hp - z.dmg);
              addFloatingText(state.playerX, state.playerY - 54, `-${z.dmg}`, "#ef4444");
              AudioEngine.hit();
            }
          }
        });

        if (state.lv <= 10 && aliveZombies === 0 && !state.stationCleared) {
          onStageCleared();
        }

        // Chuyển trạm / vào Lâu Đài Boss khi đã dọn xong trạm
        if (state.lv <= 10 && state.exitReady && state.playerX >= vw - 44) {
          const nextLv = state.lv + 1;
          setupStage(nextLv, Math.min(state.maxHp, state.hp + 25));
        }

        // Cập nhật Trùm Zombie Nguyên Mẫu (chu kỳ 7s, nháy đỏ + đếm ngược 3-2-1, đỡ khiên 5s)
        const boss = state.boss;
        if (boss && boss.hp > 0) {
          boss.y = gy;
          if (boss.hitFlash > 0) boss.hitFlash -= dt;
          if (boss.slowTimer > 0) boss.slowTimer -= dt;

          if (boss.shieldWindowTimer > 0) {
            boss.shieldWindowTimer = Math.max(0, boss.shieldWindowTimer - dt);
            if (boss.shieldWindowTimer === 0) {
              boss.cycleTimer = 7.0;
              boss.slamFired = false;
              boss.telegraphing = false;
            }
          } else {
            const spdMod = boss.slowTimer > 0 ? 0.35 : 1;
            boss.cycleTimer -= dt * spdMod;

            // Di chuyển chậm rãi áp sát nếu còn xa
            const dist = boss.x - state.playerX;
            if (dist > 135 && boss.cycleTimer > 3.2) {
              boss.x -= 28 * spdMod * dt;
            }

            if (boss.cycleTimer <= 3.0 && !boss.telegraphing) {
              boss.telegraphing = true;
              AudioEngine.alarm();
            }

            if (boss.cycleTimer <= 0 && !boss.slamFired) {
              boss.slamFired = true;
              const blocking = state.hasCastleShield || state.shieldActiveTimer > 0;
              if (blocking) {
                // Đỡ thành công -> mở cửa sổ đỡ khiên 5 giây để đồng minh núp sau khiên vừa núp vừa bắn
                boss.shieldWindowTimer = 5.0;
                AudioEngine.shield();
                spawnBurst(state.playerX + 24, gy - 32, "#38bdf8", 12);
                addFloatingText(state.playerX, gy - 72, "🛡️ ĐỠ ĐÒN 5S! ĐỒNG MINH BẮN!", "#38bdf8");
              } else {
                state.hp = Math.max(0, state.hp - 45);
                boss.cycleTimer = 7.0;
                boss.slamFired = false;
                boss.telegraphing = false;
                AudioEngine.hit();
                addFloatingText(state.playerX, gy - 68, "💥 MŨI KHOAN TRÚNG ĐÒN -45!", "#ef4444");
              }
            }
          }
        }

        // Đồng minh AI (núp sau khiên vừa núp vừa bắn khi Boss đang trong pha đỡ khiên 5s)
        state.allies.forEach((a, idx) => {
          a.y = gy;
          a.atkCd -= dt;
          const shieldingBossPhase = Boolean(boss && boss.hp > 0 && boss.shieldWindowTimer > 0);
          a.hiding = shieldingBossPhase;

          const desiredX = shieldingBossPhase
            ? Math.max(24, state.playerX - 24 - idx * 20)
            : Math.max(24, state.playerX - 42 - idx * 26);
          a.x += (desiredX - a.x) * Math.min(1, dt * 6);

          if (a.atkCd <= 0) {
            a.atkCd = shieldingBossPhase ? 0.45 : 0.9;
            const hasTarget =
              (boss && boss.hp > 0) || state.zombies.some((z) => z.hp > 0);
            if (hasTarget) {
              state.projectiles.push({
                x: a.x + 14,
                y: a.y - 30,
                vx: 520,
                dmg: shieldingBossPhase ? 18 : 11,
                color: shieldingBossPhase ? "#4ade80" : "#93c5fd",
                life: 0.9,
                fromAlly: true
              });
            }
          }
        });

        // Hạt hiệu ứng & chữ nổi
        state.particles.forEach((p) => {
          p.x += p.vx * dt;
          p.y += p.vy * dt;
          p.vy += 220 * dt;
          p.life -= dt;
        });
        state.particles = state.particles.filter((p) => p.life > 0);

        state.floatingTexts.forEach((t) => {
          t.y -= 28 * dt;
          t.life -= dt;
        });
        state.floatingTexts = state.floatingTexts.filter((t) => t.life > 0);

        if (state.hp <= 0) {
          state.mode = "gameover";
          state.attackHeld = false;
          clearUnfinishedRun();
          showToast("💀 Bạn đã gục ngã! Về sảnh để thử lại nhé.", 2600);
          setTimeout(() => {
            if (state.mode === "gameover") goToLobby();
          }, 1500);
        }

        updateHudDOM();
      }

      function updateHudDOM() {
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;
        document.getElementById("hudClassLabel").textContent = cDef.name;
        document.getElementById("hudClassLabel").style.color = cDef.color;
        document.getElementById("hudAllyLabel").textContent = `🤝 ${state.allies.length}/3 Đồng Minh`;
        document.getElementById("hudStageLabel").textContent =
          state.lv <= 10 ? `Trạm ${state.lv} / 10` : "🏰 Lâu Đài Trùm Nguyên Mẫu";

        const hpPct = Math.max(0, Math.min(100, (state.hp / state.maxHp) * 100));
        document.getElementById("hudHpText").textContent = `${Math.ceil(state.hp)} / ${state.maxHp} HP`;
        document.getElementById("hudHpBar").style.width = `${hpPct}%`;

        const waterWrap = document.getElementById("hudWaterWrap");
        if (saveData.selectedClass === "plumber") {
          waterWrap.style.display = "block";
          document.getElementById("hudWaterBar").style.width = `${Math.max(0, Math.min(100, state.waterMeter))}%`;
          document.getElementById("hudWaterText").textContent = state.waterRecharging
            ? `Nạp ${Math.ceil(state.waterRechargeTimer)}s`
            : `${Math.ceil(state.waterMeter)}% (${state.plumberMode === "laser" ? "Laser" : "Ống"})`;
        } else {
          waterWrap.style.display = "none";
        }

        if (state.boss) {
          const bPct = Math.max(0, Math.min(100, (state.boss.hp / state.boss.maxHp) * 100));
          document.getElementById("hudBossHpText").textContent = `${Math.ceil(state.boss.hp)} / ${state.boss.maxHp} HP`;
          document.getElementById("hudBossBar").style.width = `${bPct}%`;

          const cycleEl = document.getElementById("hudBossCycleText");
          if (state.boss.shieldWindowTimer > 0) {
            cycleEl.textContent = `🛡️ Đang đỡ khiên (${state.boss.shieldWindowTimer.toFixed(1)}s) — Đồng minh bắn!`;
            cycleEl.style.color = "#4ade80";
          } else if (state.boss.cycleTimer <= 3.0) {
            const countNum = Math.max(1, Math.ceil(state.boss.cycleTimer));
            cycleEl.textContent = `⚠️ CẢNH BÁO ĐÒN KHOAN: ${countNum}!`;
            cycleEl.style.color = "#f87171";
          } else {
            cycleEl.textContent = `Nhịp tấn công tiếp theo: ${state.boss.cycleTimer.toFixed(1)}s / 7.0s`;
            cycleEl.style.color = "#fde68a";
          }
        }

        const sgBtn = document.getElementById("btnShotgun");
        if (sgBtn) sgBtn.disabled = state.shotgunCd > 0;

        const shBtn = document.getElementById("btnShield");
        if (shBtn) {
          shBtn.disabled = state.shieldCdTimer > 0;
          shBtn.textContent = state.shieldActiveTimer > 0
            ? `🛡️ CHẶN (${state.shieldActiveTimer.toFixed(1)}s)`
            : state.shieldCdTimer > 0
              ? `🛡️ HỒI ${state.shieldCdTimer.toFixed(1)}s`
              : "🛡️ KHIÊN 5S";
        }

        const mtBtn = document.getElementById("btnMamTom");
        if (mtBtn) {
          mtBtn.disabled = state.mamTomCd > 0;
          mtBtn.textContent = state.mamTomCd > 0 ? `🫙 ${Math.ceil(state.mamTomCd)}s` : "🫙 MẮM TÔM";
        }

        const exBtn = document.getElementById("btnExciter");
        if (exBtn) {
          exBtn.disabled = state.exciterCd > 0;
          exBtn.textContent = state.exciterCd > 0 ? `🏍️ ${Math.ceil(state.exciterCd)}s` : "🏍️ EXCITER";
        }
      }

      function drawStickman(x, y, color, facing = 1, options = {}) {
        ctx.save();
        ctx.translate(x, y);

        if (options.hiding) {
          // Núp sau khiên
          ctx.scale(0.82, 0.82);
        }

        ctx.strokeStyle = color;
        ctx.fillStyle = color;
        ctx.lineWidth = 3.2;
        ctx.lineCap = "round";

        // Đầu
        ctx.beginPath();
        ctx.arc(0, -44, 8, 0, Math.PI * 2);
        ctx.stroke();

        // Thân
        ctx.beginPath();
        ctx.moveTo(0, -36);
        ctx.lineTo(0, -16);
        ctx.stroke();

        // Tay
        const swing = options.swingAngle || 0;
        ctx.beginPath();
        ctx.moveTo(0, -31);
        ctx.lineTo(facing * 14, -25 + Math.sin(swing) * 8);
        ctx.stroke();

        // Chân
        ctx.beginPath();
        ctx.moveTo(0, -16);
        ctx.lineTo(-8, 0);
        ctx.moveTo(0, -16);
        ctx.lineTo(8, 0);
        ctx.stroke();

        // Khiên chắn
        if (options.hasShield) {
          ctx.fillStyle = "rgba(56, 189, 248, 0.35)";
          ctx.strokeStyle = "#38bdf8";
          ctx.lineWidth = 2.5;
          ctx.beginPath();
          ctx.roundRect(facing * 14 - 4, -40, 8, 30, 3);
          ctx.fill();
          ctx.stroke();
        }

        // Báng súng / vũ khí khi đập khóa lồng
        if (options.rifleButtSwing) {
          ctx.save();
          ctx.translate(facing * 10, -28);
          ctx.rotate(options.rifleButtSwing);
          ctx.strokeStyle = "#cbd5e1";
          ctx.lineWidth = 5;
          ctx.beginPath();
          ctx.moveTo(-8, 0);
          ctx.lineTo(18, 0);
          ctx.stroke();
          ctx.restore();
        }

        ctx.restore();
      }

      function drawZombie(z) {
        ctx.save();
        ctx.translate(z.x, z.y);
        const col = z.hitFlash > 0 ? "#ffffff" : z.slowTimer > 0 ? "#a3e635" : "#84cc16";
        ctx.strokeStyle = col;
        ctx.fillStyle = col;
        ctx.lineWidth = 3;

        ctx.beginPath();
        ctx.arc(0, -42, 7.5, 0, Math.PI * 2);
        ctx.stroke();

        ctx.beginPath();
        ctx.moveTo(0, -34.5);
        ctx.lineTo(0, -15);
        ctx.moveTo(0, -29);
        ctx.lineTo(-11, -22);
        ctx.moveTo(0, -15);
        ctx.lineTo(-7, 0);
        ctx.moveTo(0, -15);
        ctx.lineTo(7, 0);
        ctx.stroke();

        ctx.restore();
      }

      function drawPrototypeBoss(boss) {
        ctx.save();
        ctx.translate(boss.x, boss.y);

        // Nháy đỏ cảnh báo trong 3 giây cuối trước khi tung đòn
        const flashRed = boss.telegraphing && Math.floor(boss.cycleTimer * 10) % 2 === 0;
        const bodyCol = boss.hitFlash > 0 ? "#ffffff" : flashRed ? "#ef4444" : "#6b21a8";

        ctx.strokeStyle = bodyCol;
        ctx.fillStyle = bodyCol;
        ctx.lineWidth = 5.5;

        // Thân & đầu to lớn cơ bắp
        ctx.beginPath();
        ctx.arc(0, -76, 15, 0, Math.PI * 2);
        ctx.stroke();

        ctx.beginPath();
        ctx.moveTo(0, -61);
        ctx.lineTo(0, -24);
        ctx.moveTo(0, -24);
        ctx.lineTo(-15, 0);
        ctx.moveTo(0, -24);
        ctx.lineTo(15, 0);
        ctx.stroke();

        // 1 mắt người máy đỏ
        ctx.fillStyle = "#ff2a55";
        ctx.beginPath();
        ctx.arc(-5, -77, 4.5, 0, Math.PI * 2);
        ctx.fill();

        // Tay trái cơ bắp
        ctx.strokeStyle = flashRed ? "#fca5a5" : "#9333ea";
        ctx.beginPath();
        ctx.moveTo(0, -52);
        ctx.lineTo(-22, -34);
        ctx.stroke();

        // 1 cánh tay mũi khoan bên trái hướng tới người chơi
        const drillOffset = boss.telegraphing ? -14 : 0;
        ctx.save();
        ctx.translate(-14 + drillOffset, -44);
        ctx.fillStyle = "#e2e8f0";
        ctx.beginPath();
        ctx.moveTo(0, -8);
        ctx.lineTo(-28, 0);
        ctx.lineTo(0, 8);
        ctx.closePath();
        ctx.fill();
        ctx.restore();

        ctx.restore();
      }

      function drawGeminiCage(x, y, lockBroken, geminiStep) {
        ctx.save();
        ctx.translate(x, y);

        // Khung lồng sắt
        ctx.strokeStyle = "#cbd5e1";
        ctx.lineWidth = 2.5;
        ctx.strokeRect(-22, -46, 44, 46);
        for (let bx = -14; bx <= 14; bx += 7) {
          ctx.beginPath();
          ctx.moveTo(bx, -46);
          ctx.lineTo(bx, 0);
          ctx.stroke();
        }

        // Khóa lồng
        if (!lockBroken) {
          ctx.fillStyle = "#f59e0b";
          ctx.fillRect(-26, -26, 9, 11);
        }

        // Biểu tượng Gemini gắn tay chân người que
        const gx = lockBroken && geminiStep === 2 ? -42 : 0;
        const gyOffset = lockBroken && geminiStep === 2 ? Math.sin(state.cutsceneTimer * 12) * 3 : 0;

        ctx.save();
        ctx.translate(gx, -22 + gyOffset);

        // Tay chân người que gắn vào biểu tượng Gemini
        ctx.strokeStyle = "#93c5fd";
        ctx.lineWidth = 2.5;
        ctx.beginPath();
        ctx.moveTo(-10, 0);
        ctx.lineTo(-17, -6);
        ctx.moveTo(10, 0);
        ctx.lineTo(17, -6);
        ctx.moveTo(-4, 10);
        ctx.lineTo(-8, 22);
        ctx.moveTo(4, 10);
        ctx.lineTo(8, 22);
        ctx.stroke();

        // Biểu tượng 4 cánh lấp lánh của Gemini
        ctx.fillStyle = "#38bdf8";
        ctx.beginPath();
        ctx.moveTo(0, -12);
        ctx.quadraticCurveTo(3, -3, 12, 0);
        ctx.quadraticCurveTo(3, 3, 0, 12);
        ctx.quadraticCurveTo(-3, 3, -12, 0);
        ctx.quadraticCurveTo(-3, -3, 0, -12);
        ctx.fill();

        ctx.restore();
        ctx.restore();
      }

      function renderHillEnding() {
        const vw = getViewWidth();
        const gy = getGroundY();

        // Bầu trời bình minh ấm áp
        const sky = ctx.createLinearGradient(0, 0, 0, gy);
        sky.addColorStop(0, "#1e1b4b");
        sky.addColorStop(0.45, "#be185d");
        sky.addColorStop(0.8, "#fb923c");
        sky.addColorStop(1, "#fde047");
        ctx.fillStyle = sky;
        ctx.fillRect(0, 0, vw, gy + 140);

        // Mặt trời bình minh
        ctx.fillStyle = "#fef08a";
        ctx.beginPath();
        ctx.arc(vw * 0.5, gy - 70, 38, 0, Math.PI * 2);
        ctx.fill();

        // Ngọn đồi xanh tối
        ctx.fillStyle = "#14532d";
        ctx.beginPath();
        ctx.moveTo(0, gy + 140);
        ctx.quadraticCurveTo(vw * 0.5, gy - 32, vw, gy + 140);
        ctx.closePath();
        ctx.fill();

        const hillY = gy - 8;
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;

        // Nhóm nhân vật chính + Gemini ngồi trên đồi ngắm bình minh
        drawStickman(vw * 0.34, hillY, cDef.color, 1);
        state.allies.forEach((a, i) => {
          const rDef = CLASS_DEFS[a.role] || CLASS_DEFS.survivor;
          drawStickman(vw * 0.24 + i * 26, hillY, rDef.color, 1);
        });

        // Gemini người que ngồi ngắm bình minh cạnh nhóm
        ctx.save();
        ctx.translate(vw * 0.44, hillY - 14);
        ctx.strokeStyle = "#e2e8f0";
        ctx.lineWidth = 2.5;
        ctx.beginPath();
        ctx.moveTo(-6, 12);
        ctx.lineTo(-10, 14);
        ctx.moveTo(6, 12);
        ctx.lineTo(10, 14);
        ctx.stroke();
        ctx.fillStyle = "#38bdf8";
        ctx.beginPath();
        ctx.moveTo(0, -10);
        ctx.quadraticCurveTo(3, -3, 10, 0);
        ctx.quadraticCurveTo(3, 3, 0, 10);
        ctx.quadraticCurveTo(-3, 3, -10, 0);
        ctx.quadraticCurveTo(-3, -3, 0, -10);
        ctx.fill();
        ctx.restore();

        // Cây súng shotgun và chai mắm tôm vứt sang một bên
        ctx.save();
        ctx.translate(vw * 0.58, hillY + 4);
        // Shotgun nằm ngang
        ctx.strokeStyle = "#475569";
        ctx.lineWidth = 5;
        ctx.beginPath();
        ctx.moveTo(-18, 2);
        ctx.lineTo(16, -2);
        ctx.stroke();
        ctx.fillStyle = "#92400e";
        ctx.fillRect(-20, -2, 8, 6);

        // Chai mắm tôm nằm nghiêng bên cạnh
        ctx.translate(34, 2);
        ctx.rotate(0.45);
        ctx.fillStyle = "#7e22ce";
        ctx.fillRect(-5, -9, 10, 16);
        ctx.fillStyle = "#facc15";
        ctx.fillRect(-3, -13, 6, 4);
        ctx.restore();

        // Pháo hoa rực rỡ
        state.fireworks.forEach((fw) => {
          const ratio = fw.age / fw.maxAge;
          const radius = 14 + ratio * 58;
          ctx.save();
          ctx.globalAlpha = Math.max(0, 1 - ratio);
          ctx.strokeStyle = fw.color;
          ctx.lineWidth = 2.5;
          for (let k = 0; k < 12; k++) {
            const ang = (Math.PI * 2 * k) / 12;
            ctx.beginPath();
            ctx.moveTo(fw.x + Math.cos(ang) * (radius * 0.35), fw.y + Math.sin(ang) * (radius * 0.35));
            ctx.lineTo(fw.x + Math.cos(ang) * radius, fw.y + Math.sin(ang) * radius);
            ctx.stroke();
          }
          ctx.restore();
        });

        // Dòng chữ cảm ơn vì đã chơi
        ctx.save();
        ctx.fillStyle = "#ffffff";
        ctx.strokeStyle = "rgba(15, 23, 42, 0.75)";
        ctx.lineWidth = 4;
        ctx.font = "900 22px system-ui, sans-serif";
        ctx.textAlign = "center";
        const msg = "🎉 CẢM ƠN VÌ ĐÃ CHƠI! 🎉";
        ctx.strokeText(msg, vw * 0.5, 92);
        ctx.fillText(msg, vw * 0.5, 92);
        ctx.restore();
      }

      function render() {
        const vw = getViewWidth();
        const rect = gameScreen.getBoundingClientRect();
        const gy = getGroundY();

        ctx.clearRect(0, 0, vw, rect.height);

        if (state.mode === "hill_ending") {
          renderHillEnding();
          return;
        }

        // Nền đêm tối
        const bgGrad = ctx.createLinearGradient(0, 0, 0, gy);
        bgGrad.addColorStop(0, state.lv === 11 ? "#1b1035" : "#0a1024");
        bgGrad.addColorStop(1, state.lv === 11 ? "#2e1065" : "#111b38");
        ctx.fillStyle = bgGrad;
        ctx.fillRect(0, 0, vw, gy);

        // Mặt đất
        ctx.fillStyle = "#1e293b";
        ctx.fillRect(0, gy, vw, rect.height - gy);
        ctx.strokeStyle = "#475569";
        ctx.lineWidth = 2;
        ctx.beginPath();
        ctx.moveTo(0, gy);
        ctx.lineTo(vw, gy);
        ctx.stroke();

        // Cổng chuyển trạm khi dọn xong trạm 1..10
        if (state.lv <= 10 && state.exitReady) {
          ctx.fillStyle = "rgba(34, 197, 94, 0.25)";
          ctx.fillRect(vw - 38, gy - 66, 30, 66);
          ctx.fillStyle = "#86efac";
          ctx.font = "800 11px system-ui, sans-serif";
          ctx.textAlign = "center";
          ctx.fillText("TIẾP ▶", vw - 23, gy - 72);
        }

        // Vật phẩm / rương / giải cứu / khiên
        state.pickups.forEach((p) => {
          if (p.collected) return;
          ctx.save();
          ctx.translate(p.x, p.y);
          if (p.type === "crate") {
            ctx.fillStyle = "#d97706";
            ctx.fillRect(-13, -12, 26, 24);
            ctx.strokeStyle = "#fde68a";
            ctx.lineWidth = 2;
            ctx.strokeRect(-13, -12, 26, 24);
          } else if (p.type === "rescue") {
            ctx.fillStyle = "#0284c7";
            ctx.beginPath();
            ctx.arc(0, 0, 14, 0, Math.PI * 2);
            ctx.fill();
            ctx.fillStyle = "#fff";
            ctx.font = "900 13px system-ui";
            ctx.textAlign = "center";
            ctx.fillText("+", 0, 5);
          } else if (p.type === "shield") {
            ctx.fillStyle = "#38bdf8";
            ctx.beginPath();
            ctx.moveTo(0, -15);
            ctx.lineTo(13, -8);
            ctx.lineTo(10, 10);
            ctx.lineTo(0, 16);
            ctx.lineTo(-10, 10);
            ctx.lineTo(-13, -8);
            ctx.closePath();
            ctx.fill();
          } else if (p.type === "heal") {
            ctx.fillStyle = "#22c55e";
            ctx.beginPath();
            ctx.arc(0, 0, 9, 0, Math.PI * 2);
            ctx.fill();
          }
          ctx.restore();
        });

        // Tia nước Laser nếu Thợ Sửa Ống Nước đang bật
        if (
          state.mode === "playing" &&
          saveData.selectedClass === "plumber" &&
          state.plumberMode === "laser" &&
          !state.waterRecharging
        ) {
          ctx.save();
          const startX = state.playerX + state.facing * 18;
          const beamW = state.facing * 190;
          ctx.fillStyle = "rgba(56, 189, 248, 0.45)";
          ctx.fillRect(Math.min(startX, startX + beamW), state.playerY - 40, Math.abs(beamW), 16);
          ctx.restore();
        }

        // Đồng minh AI
        state.allies.forEach((a) => {
          const rDef = CLASS_DEFS[a.role] || CLASS_DEFS.survivor;
          drawStickman(a.x, a.y, rDef.color, 1, {
            hiding: a.hiding,
            swingAngle: state.mode === "rescue_cutscene" ? state.cutsceneTimer * 8 : 0
          });
        });

        // Nhân vật chính
        const cDef = CLASS_DEFS[saveData.selectedClass] || CLASS_DEFS.survivor;
        const rifleSwing =
          state.mode === "rescue_cutscene" && state.cutsceneStep === 1
            ? Math.sin(state.smashSwingTimer * 16) * 0.9 - 0.3
            : 0;
        drawStickman(state.playerX, state.playerY, cDef.color, state.facing, {
          hasShield: state.shieldActiveTimer > 0 || state.hasCastleShield,
          swingAngle: state.meleeCd > 0 ? 1.1 : 0,
          rifleButtSwing: rifleSwing
        });

        // Lồng sắt có biểu tượng Gemini trong cảnh giải cứu
        if (state.mode === "rescue_cutscene") {
          drawGeminiCage(state.cageX, state.cageY, state.cageLockBroken, state.cutsceneStep);
        }

        // Zombie thường
        state.zombies.forEach((z) => {
          if (z.hp > 0) drawZombie(z);
        });

        // Trùm Zombie Nguyên Mẫu
        if (state.boss && state.boss.hp > 0) {
          drawPrototypeBoss(state.boss);
        }

        // Đạn
        state.projectiles.forEach((pr) => {
          ctx.fillStyle = pr.color || "#f8fafc";
          ctx.beginPath();
          ctx.arc(pr.x, pr.y, 4.5, 0, Math.PI * 2);
          ctx.fill();
        });

        // Hạt
        state.particles.forEach((p) => {
          ctx.fillStyle = p.color;
          ctx.fillRect(p.x - 2.5, p.y - 2.5, 5, 5);
        });

        // Chữ nổi
        state.floatingTexts.forEach((t) => {
          ctx.save();
          ctx.fillStyle = t.color;
          ctx.font = "900 13px system-ui, sans-serif";
          ctx.textAlign = "center";
          ctx.fillText(t.text, t.x, t.y);
          ctx.restore();
        });
      }

      // GẮN SỰ KIỆN SẢNH & MODAL
      document.getElementById("btnPlay").addEventListener("click", () => {
        if (saveData.unfinishedRun) {
          resumeSavedRun();
        } else {
          startFreshGame(1);
        }
      });

      document.getElementById("btnOpenLv").addEventListener("click", () => {
        renderLvModal();
        openModal(lvModal);
      });

      document.getElementById("btnOpenClasses").addEventListener("click", () => {
        renderClassModal();
        openModal(classModal);
      });

      document.getElementById("closeClassModal").addEventListener("click", () => closeModal(classModal));
      document.getElementById("closeLvModal").addEventListener("click", () => closeModal(lvModal));

      [classModal, lvModal].forEach((m) => {
        m.addEventListener("click", (e) => {
          if (e.target === m) closeModal(m);
        });
      });

      function toggleSound() {
        state.soundEnabled = !state.soundEnabled;
        refreshLobbyUI();
      }

      document.getElementById("btnSound").addEventListener("click", toggleSound);
      document.getElementById("btnIngameSound").addEventListener("click", toggleSound);

      document.getElementById("btnResetSave").addEventListener("click", () => {
        const fresh = defaultSave();
        Object.assign(saveData, fresh);
        persistSave();
        refreshLobbyUI();
        showToast("Đã reset dữ liệu lưu!", 1500);
      });

      document.getElementById("btnPauseLobby").addEventListener("click", goToLobby);
      document.getElementById("btnBackLobbyEnd").addEventListener("click", goToLobby);
      document.getElementById("btnPlayAgainEnd").addEventListener("click", () => {
        endingOverlay.classList.remove("open");
        startFreshGame(1);
      });

      // ĐIỀU KHIỂN DI CHUYỂN & PHÍM BẤM
      const bindMoveBtn = (el, prop) => {
        el.addEventListener("pointerdown", (e) => {
          e.preventDefault();
          state[prop] = true;
        });
        el.addEventListener("pointerup", () => { state[prop] = false; });
        el.addEventListener("pointerleave", () => { state[prop] = false; });
        el.addEventListener("pointercancel", () => { state[prop] = false; });
      };

      bindMoveBtn(document.getElementById("btnLeft"), "moveLeft");
      bindMoveBtn(document.getElementById("btnRight"), "moveRight");

      window.addEventListener("keydown", (e) => {
        if (e.key === "ArrowLeft" || e.key === "a" || e.key === "A") state.moveLeft = true;
        if (e.key === "ArrowRight" || e.key === "d" || e.key === "D") state.moveRight = true;
        if (e.key === " " || e.key === "j" || e.key === "J") {
          state.attackHeld = true;
          triggerPrimaryAttack();
        }
      });

      window.addEventListener("keyup", (e) => {
        if (e.key === "ArrowLeft" || e.key === "a" || e.key === "A") state.moveLeft = false;
        if (e.key === "ArrowRight" || e.key === "d" || e.key === "D") state.moveRight = false;
        if (e.key === " " || e.key === "j" || e.key === "J") state.attackHeld = false;
      });

      window.addEventListener("resize", resizeCanvas);

      // VÒNG LẶP CHÍNH
      let lastTime = performance.now();
      function loop(now) {
        const dt = Math.min(0.05, Math.max(0.001, (now - lastTime) / 1000));
        lastTime = now;

        if (state.mode !== "lobby") {
          update(dt);
          render();
        }

        requestAnimationFrame(loop);
      }

      refreshLobbyUI();
      requestAnimationFrame(loop);
    })();
  </script>
</body>
</html>
