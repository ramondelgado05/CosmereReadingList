<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Cosmere Progress Tracker</title>
  <meta name="viewport"
        content="width=device-width, initial-scale=1.0, maximum-scale=1.0, viewport-fit=cover" />
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <style>
    :root {
      --primary: #b11226;
      --primary-dark: #7f0c1b;
      --accent: #0a3648;
      --bg: #05060a;
      --bg-elevated: #0b0d14;
      --card-bg: #10121b;
      --text: #f5f5f7;
      --text-muted: #a0a3b1;
      --border-subtle: rgba(255, 255, 255, 0.06);
      --shadow-soft: 0 18px 40px rgba(0, 0, 0, 0.6);
      --pill-bg: rgba(255, 255, 255, 0.04);
      --pill-border: rgba(255, 255, 255, 0.08);
    }

    * {
      box-sizing: border-box;
    }

    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text", sans-serif;
      background: radial-gradient(circle at top, #182038 0, #05060a 55%);
      color: var(--text);
      -webkit-font-smoothing: antialiased;
    }

    body {
      display: flex;
      justify-content: center;
      align-items: stretch;
      padding: env(safe-area-inset-top) env(safe-area-inset-right)
               env(safe-area-inset-bottom) env(safe-area-inset-left);
    }

    .app-shell {
      width: 100%;
      max-width: 480px;
      padding: 16px;
      display: flex;
      justify-content: center;
      align-items: stretch;
    }

    .app {
      background: linear-gradient(145deg, rgba(11, 13, 20, 0.98), rgba(4, 6, 12, 0.98));
      border-radius: 24px;
      width: 100%;
      padding: 18px 16px 20px;
      box-shadow: var(--shadow-soft);
      border: 1px solid rgba(255, 255, 255, 0.08);
      display: flex;
      flex-direction: column;
      gap: 14px;
      max-height: calc(100vh - 32px - env(safe-area-inset-top) - env(safe-area-inset-bottom));
      overflow: hidden;
    }

    .app-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .app-title-block {
      display: flex;
      flex-direction: column;
      gap: 3px;
    }

    .app-title {
      font-size: 1.2rem;
      font-weight: 600;
      letter-spacing: 0.02em;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .badge {
      font-size: 0.65rem;
      padding: 2px 6px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.16);
      background: radial-gradient(circle at top, rgba(255, 255, 255, 0.08), rgba(0, 0, 0, 0.6));
      color: var(--text-muted);
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    .cosmere-dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: linear-gradient(135deg, #f5e6c8, #c9963f);
      box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.8);
    }

    .app-subtitle {
      margin: 0;
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .app-pill {
      display: flex;
      align-items: center;
      gap: 6px;
      padding: 6px 10px;
      border-radius: 999px;
      border: 1px solid var(--pill-border);
      background: radial-gradient(circle at top left, rgba(255, 255, 255, 0.08), rgba(3, 4, 9, 0.9));
      font-size: 0.75rem;
      color: var(--text-muted);
      white-space: nowrap;
    }

    .app-pill span:first-child {
      font-size: 0.9rem;
    }

    .main-scroll {
      flex: 1;
      overflow-y: auto;
      padding-right: 4px;
      margin-right: -4px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      padding-top: 6px;
    }

    .card {
      background: radial-gradient(circle at top left, rgba(255, 255, 255, 0.04), rgba(8, 10, 19, 0.98));
      border-radius: 18px;
      padding: 12px 12px 12px;
      border: 1px solid var(--border-subtle);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
    }

    .card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 8px;
      gap: 8px;
    }

    .section-title {
      font-size: 0.86rem;
      font-weight: 600;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      color: #e8e9f3;
    }

    .section-subtitle {
      font-size: 0.75rem;
      color: var(--text-muted);
    }

    .config-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 8px;
      margin-bottom: 8px;
    }

    .field {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    label {
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.07em;
      color: var(--text-muted);
    }

    input[type="date"],
    input[type="number"] {
      width: 100%;
      padding: 6px 8px;
      border-radius: 10px;
      border: 1px solid rgba(255, 255, 255, 0.16);
      background: rgba(2, 4, 12, 0.95);
      color: var(--text);
      font-size: 0.8rem;
      outline: none;
      -webkit-appearance: none;
    }

    input[type="number"]::-webkit-outer-spin-button,
    input[type="number"]::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }

    input[type="number"] {
      -moz-appearance: textfield;
    }

    input::placeholder {
      color: rgba(160, 163, 177, 0.8);
    }

    .btn-row {
      display: flex;
      gap: 8px;
      margin-top: 8px;
      flex-wrap: wrap;
    }

    .btn {
      display: inline-flex;
      justify-content: center;
      align-items: center;
      gap: 6px;
      padding: 6px 10px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.12);
      background: radial-gradient(circle at top left, rgba(255, 255, 255, 0.08), rgba(2, 4, 10, 0.95));
      color: var(--text);
      font-size: 0.78rem;
      cursor: pointer;
      transition: transform 0.08s ease-out, box-shadow 0.08s ease-out, background 0.12s;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      border-color: rgba(255, 255, 255, 0.18);
      box-shadow: 0 8px 20px rgba(177, 18, 38, 0.45);
    }

    .btn-destructive {
      background: linear-gradient(135deg, #261019, #3a101f);
      border-color: rgba(255, 255, 255, 0.16);
      color: #ffd7dd;
    }

    .btn-secondary {
      background: rgba(255, 255, 255, 0.03);
    }

    .btn:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 24px rgba(0, 0, 0, 0.55);
    }

    .btn:active {
      transform: translateY(0);
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.5);
    }

    .btn span:first-child {
      font-size: 0.9rem;
    }

    .btn span:last-child {
      white-space: nowrap;
    }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 8px;
      margin-top: 4px;
    }

    .stat-pill {
      border-radius: 14px;
      padding: 8px 10px;
      background: rgba(7, 8, 16, 0.95);
      border: 1px solid rgba(255, 255, 255, 0.08);
      display: flex;
      flex-direction: column;
      gap: 2px;
      min-height: 52px;
    }

    .stat-label {
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      color: var(--text-muted);
    }

    .stat-value {
      font-size: 0.96rem;
      font-weight: 600;
    }

    .stat-sub {
      font-size: 0.72rem;
      color: var(--text-muted);
    }

    .progress-block {
      margin-top: 10px;
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .progress-label {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      font-size: 0.75rem;
      color: var(--text-muted);
    }

    .progress-outer {
      width: 100%;
      height: 8px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.06);
      overflow: hidden;
      position: relative;
    }

    .progress-inner {
      position: absolute;
      inset: 0;
      width: 0%;
      background: linear-gradient(90deg, #b11226, #f9a825);
      border-radius: inherit;
      transition: width 0.3s ease-out;
    }

    .status-pill {
      margin-top: 8px;
      padding: 7px 10px;
      border-radius: 999px;
      font-size: 0.75rem;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      border: 1px solid rgba(255, 255, 255, 0.12);
      background: rgba(0, 0, 0, 0.4);
    }

    .status-pill.status-ahead {
      border-color: rgba(120, 220, 150, 0.7);
      background: radial-gradient(circle at top left, rgba(88, 199, 132, 0.3), rgba(0, 0, 0, 0.4));
    }

    .status-pill.status-behind {
      border-color: rgba(255, 181, 102, 0.7);
      background: radial-gradient(circle at top left, rgba(255, 171, 64, 0.28), rgba(0, 0, 0, 0.4));
    }

    .status-pill.status-ontrack {
      border-color: rgba(129, 212, 250, 0.7);
      background: radial-gradient(circle at top left, rgba(79, 195, 247, 0.32), rgba(0, 0, 0, 0.4));
    }

    .log-input-row {
      display: grid;
      grid-template-columns: 2fr 3fr;
      gap: 8px;
      align-items: center;
      margin-top: 4px;
    }

    .inline-note {
      font-size: 0.72rem;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .today-info {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .log-table {
      margin-top: 8px;
      max-height: 220px;
      overflow-y: auto;
      border-radius: 12px;
      border: 1px solid rgba(255, 255, 255, 0.06);
      background: rgba(4, 6, 12, 0.92);
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.78rem;
    }

    thead {
      position: sticky;
      top: 0;
      background: rgba(11, 13, 20, 0.98);
      z-index: 1;
    }

    th, td {
      padding: 6px 8px;
      text-align: left;
      border-bottom: 1px solid rgba(255, 255, 255, 0.04);
      white-space: nowrap;
    }

    th {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-muted);
    }

    tbody tr:last-child td {
      border-bottom: none;
    }

    tbody tr:nth-child(even) {
      background: rgba(255, 255, 255, 0.01);
    }

    .empty-state {
      padding: 10px;
      font-size: 0.78rem;
      color: var(--text-muted);
      text-align: center;
    }

    .footer {
      font-size: 0.7rem;
      color: var(--text-muted);
      text-align: center;
      padding-top: 4px;
    }

    .footer span {
      opacity: 0.9;
    }

    .footer-emphasis {
      color: #f5e6c8;
    }

    .section-description {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    .book-list {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 8px;
    }

    .book-row {
      display: flex;
      flex-direction: column;
      gap: 6px;
      padding: 8px 10px;
      border-radius: 10px;
      background: rgba(255, 255, 255, 0.02);
      border: 1px solid var(--border-subtle);
    }

    .book-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 8px;
      flex-wrap: wrap;
    }

    .book-title {
      font-size: 0.9rem;
      font-weight: 500;
    }

    .book-meta {
      font-size: 0.75rem;
      color: var(--text-muted);
      text-align: right;
    }

    .book-progress-outer {
      position: relative;
      width: 100%;
      height: 6px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.06);
      overflow: hidden;
    }

    .book-progress-inner {
      position: absolute;
      inset: 0;
      width: 0%;
      background: linear-gradient(90deg, #b11226, #f9a825);
      border-radius: inherit;
      transition: width 0.3s ease-out;
    }

    @media (max-width: 420px) {
      .app {
        padding: 14px 12px 16px;
        border-radius: 20px;
      }
      .app-title {
        font-size: 1.1rem;
      }
      .config-grid {
        grid-template-columns: 1fr;
      }
      .stats-row {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <div class="app-shell">
    <div class="app">
      <header class="app-header">
        <div class="app-title-block">
          <div class="app-title">
            <span>Cosmere Tracker</span>
            <span class="badge">
              <span class="cosmere-dot"></span>
              <span>Year-long read</span>
            </span>
          </div>
          <p class="app-subtitle" id="appSubtitle">Loading plan…</p>
        </div>
        <div class="pill app-pill">
          <span>📚</span>
          <span>Keep logging, stay on pace.</span>
        </div>
      </header>

      <main class="main-scroll">
        <!-- CONFIG -->
        <section class="card">
          <div class="card-header">
            <div>
              <div class="section-title">Plan setup</div>
              <div class="section-subtitle">Your Cosmere marathon baseline</div>
            </div>
          </div>

          <div class="config-grid">
            <div class="field">
              <label for="startDate">Start date</label>
              <input id="startDate" type="date" />
            </div>
            <div class="field">
              <label for="totalHours">Total hours</label>
              <input id="totalHours" type="number" step="0.1" min="1" />
            </div>
            <div class="field">
              <label for="dailyGoal">Daily hours</label>
              <input id="dailyGoal" type="number" step="0.01" min="0.1" />
            </div>
          </div>

          <div class="btn-row">
            <button class="btn btn-primary" id="saveConfigBtn">
              <span>💾</span>
              <span>Save plan</span>
            </button>
            <button class="btn btn-secondary" id="resetAllBtn">
              <span>🧹</span>
              <span>Reset all</span>
            </button>
          </div>

          <p class="inline-note">
            Defaults to every published Cosmere novel & novella in this list, finished in 1 year.
          </p>
        </section>

        <!-- DAILY STATS -->
        <section class="card">
          <div class="card-header">
            <div>
              <div class="section-title">Today & overall</div>
              <div class="section-subtitle">Log time, watch the numbers shift</div>
            </div>
          </div>

          <div class="log-input-row">
            <div class="field">
              <label for="todayMinutes">Today&apos;s minutes</label>
              <input id="todayMinutes" type="number" step="1" min="0" placeholder="e.g. 45" />
            </div>
            <div class="btn-row" style="margin-top: 18px;">
              <button class="btn btn-primary" id="logTodayBtn">
                <span>➕</span>
                <span>Log today</span>
              </button>
              <button class="btn btn-secondary" id="clearTodayBtn">
                <span>♻️</span>
                <span>Clear today</span>
              </button>
            </div>
          </div>

          <p class="today-info" id="todayInfo"></p>

          <div class="stats-grid">
            <div class="stat-pill">
              <div class="stat-label">Total hours read</div>
              <div class="stat-value" id="statTotalHours">0 h</div>
              <div class="stat-sub" id="statTotalDays">0 days since start</div>
            </div>
            <div class="stat-pill">
              <div class="stat-label">Vs. your plan</div>
              <div class="stat-sub" id="statGoalCompare">0 h vs 0 h goal</div>
              <div class="stat-sub" id="statAheadBehind">You are basically on pace.</div>
            </div>
          </div>

          <div class="progress-block">
            <div class="progress-label">
              <span>Overall progress</span>
              <span id="statPercent">0%</span>
            </div>
            <div class="progress-outer">
              <div class="progress-inner" id="progressInner"></div>
            </div>
          </div>

          <div id="statusPill" class="status-pill status-ontrack" style="display:none;"></div>
        </section>

        <!-- BOOK PROGRESS -->
        <section class="card">
          <div class="section-title">Book-by-book progress</div>
          <p class="section-description">
            Assumes you read straight through this Cosmere list in order. You can tweak titles
            & hours in the script and the math will auto-update.
          </p>
          <div id="bookProgressList" class="book-list">
            <!-- Filled by JavaScript -->
          </div>
        </section>

        <!-- LOGS -->
        <section class="card">
          <div class="section-title">Reading log</div>
          <div class="log-table" id="logTableWrapper">
            <div class="empty-state" id="emptyLogMsg">
              No entries yet. Log your first day above. ✨
            </div>
            <table id="logTable" style="display:none;">
              <thead>
                <tr>
                  <th>Date</th>
                  <th>Minutes</th>
                  <th>Hours (cum.)</th>
                </tr>
              </thead>
              <tbody id="logTableBody"></tbody>
            </table>
          </div>
        </section>
      </main>

      <footer class="footer">
        <span>Made for a <span class="footer-emphasis">year-long Cosmere journey</span>. Adjust numbers as your TBR evolves.</span>
      </footer>
    </div>
  </div>

  <script>
    const STORAGE_KEY = 'cosmereTracker_v2';

    // Full Cosmere list (novels + novellas + White Sand + Secret Projects)
    // Hours are approximate 1x audiobook runtimes; tweak if your editions differ.
    const BOOKS = [
      // Sel
      { id: 'elantris',  title: 'Elantris', hours: 28.7 },
      { id: 'emperors_soul', title: "The Emperor's Soul", hours: 4.0 },
      { id: 'hope_elantris',  title: 'The Hope of Elantris', hours: 1.0 },

      // Mistborn Era 1
      { id: 'mistborn1', title: 'Mistborn: The Final Empire', hours: 24.5 },
      { id: 'mistborn2', title: 'Mistborn: The Well of Ascension', hours: 28.9 },
      { id: 'mistborn3', title: 'Mistborn: The Hero of Ages', hours: 27.5 },
      { id: 'eleventh_metal', title: 'The Eleventh Metal', hours: 1.0 },
      { id: 'secret_history', title: 'Mistborn: Secret History', hours: 2.9 },

      // Mistborn Era 2
      { id: 'alloy_of_law',   title: 'The Alloy of Law', hours: 12.5 },
      { id: 'shadows_of_self',title: 'Shadows of Self', hours: 13.0 },
      { id: 'bands_of_mourning', title: 'The Bands of Mourning', hours: 14.5 },
      { id: 'lost_metal',     title: 'The Lost Metal', hours: 18.4 },
      { id: 'allomancer_jak', title: 'Allomancer Jak and the Pits of Eltania', hours: 1.5 },

      // Nalthis
      { id: 'warbreaker', title: 'Warbreaker', hours: 24.9 },

      // Roshar - Stormlight Archive main & novellas
      { id: 'wok',  title: 'The Way of Kings', hours: 45.5 },
      { id: 'wor',  title: 'Words of Radiance', hours: 48.5 },
      { id: 'edgedancer', title: 'Edgedancer', hours: 7.5 },
      { id: 'oathbringer', title: 'Oathbringer', hours: 55.1 },
      { id: 'dawnshard', title: 'Dawnshard', hours: 7.1 },
      { id: 'row',  title: 'Rhythm of War', hours: 57.4 },
      { id: 'wind_truth', title: 'Wind and Truth', hours: 62.8 }, // projected / approximate

      // Threnody & Drominad
      { id: 'shadows_for_silence', title: 'Shadows for Silence in the Forests of Hell', hours: 3.7 },
      { id: 'sixth_of_dusk', title: 'Sixth of the Dusk', hours: 2.5 },

      // Taldain
      { id: 'white_sand', title: 'White Sand (omnibus / audio adaptation)', hours: 14.0 },

      // Cosmere Secret Projects
      { id: 'tress',  title: 'Tress of the Emerald Sea', hours: 12.5 },
      { id: 'yumi',   title: 'Yumi and the Nightmare Painter', hours: 15.0 },
      { id: 'sunlit', title: 'The Sunlit Man', hours: 12.0 }
    ];

    const DEFAULT_START_DATE = '2026-01-01';
    const DEFAULT_TOTAL_HOURS = BOOKS.reduce((sum, b) => sum + (b.hours || 0), 0);
    const DEFAULT_DAILY_GOAL = +(DEFAULT_TOTAL_HOURS / 365).toFixed(2);

    function getTodayISO() {
      const d = new Date();
      const offsetMs = d.getTimezoneOffset() * 60000;
      const local = new Date(d.getTime() - offsetMs);
      return local.toISOString().split('T')[0];
    }

    function loadState() {
      const raw = localStorage.getItem(STORAGE_KEY);
      if (!raw) {
        return {
          config: {
            startDate: DEFAULT_START_DATE,
            totalHours: DEFAULT_TOTAL_HOURS,
            dailyGoal: DEFAULT_DAILY_GOAL
          },
          logs: {}
        };
      }
      try {
        const parsed = JSON.parse(raw);
        if (!parsed.config) parsed.config = {};
        if (!parsed.logs) parsed.logs = {};

        parsed.config.startDate = parsed.config.startDate || DEFAULT_START_DATE;
        parsed.config.totalHours = parsed.config.totalHours || DEFAULT_TOTAL_HOURS;
        parsed.config.dailyGoal = parsed.config.dailyGoal || DEFAULT_DAILY_GOAL;

        return parsed;
      } catch (e) {
        console.error('Error parsing state, resetting.', e);
        return {
          config: {
            startDate: DEFAULT_START_DATE,
            totalHours: DEFAULT_TOTAL_HOURS,
            dailyGoal: DEFAULT_DAILY_GOAL
          },
          logs: {}
        };
      }
    }

    function saveState(state) {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
    }

    let state = loadState();

    const startDateInput = document.getElementById('startDate');
    const totalHoursInput = document.getElementById('totalHours');
    const dailyGoalInput = document.getElementById('dailyGoal');
    const todayMinutesInput = document.getElementById('todayMinutes');

    const statTotalHours = document.getElementById('statTotalHours');
    const statTotalDays = document.getElementById('statTotalDays');
    const statGoalCompare = document.getElementById('statGoalCompare');
    const statAheadBehind = document.getElementById('statAheadBehind');
    const statPercent = document.getElementById('statPercent');
    const progressInner = document.getElementById('progressInner');
    const statusPill = document.getElementById('statusPill');
    const subtitleEl = document.getElementById('appSubtitle');

    const emptyLogMsg = document.getElementById('emptyLogMsg');
    const logTable = document.getElementById('logTable');
    const logTableBody = document.getElementById('logTableBody');
    const todayInfo = document.getElementById('todayInfo');

    function initUI() {
      startDateInput.value = state.config.startDate;
      totalHoursInput.value = state.config.totalHours;
      dailyGoalInput.value = state.config.dailyGoal;

      const todayKey = getTodayISO();
      todayMinutesInput.value = state.logs[todayKey] || '';

      updateAll();
    }

    function dateDiffInDays(start, end) {
      const s = new Date(start + 'T00:00:00');
      const e = new Date(end + 'T00:00:00');
      const diffMs = e - s;
      return Math.floor(diffMs / (1000 * 60 * 60 * 24));
    }

    function computeStats() {
      const { config, logs } = state;
      const totalMinutes = Object.values(logs).reduce((sum, m) => sum + (m || 0), 0);
      const totalHours = totalMinutes / 60;

      const today = getTodayISO();
      const daysSinceStart = Math.max(0, dateDiffInDays(config.startDate, today));
      const daysWithToday = daysSinceStart + 1;

      const expectedHours = daysWithToday * config.dailyGoal;
      const aheadBehind = totalHours - expectedHours;
      const percent = Math.min(
        100,
        Math.max(0, (totalHours / config.totalHours) * 100)
      );

      return {
        totalMinutes,
        totalHours,
        daysSinceStart,
        daysWithToday,
        expectedHours,
        aheadBehind,
        percent
      };
    }

    function renderBookProgress(totalHoursRead) {
      const container = document.getElementById('bookProgressList');
      if (!container || !Array.isArray(BOOKS)) return;

      container.innerHTML = '';
      let remaining = totalHoursRead;

      for (const book of BOOKS) {
        const bookHours = book.hours || 0;
        const consumed = Math.max(0, Math.min(bookHours, remaining));
        remaining -= consumed;

        const percent = bookHours > 0 ? (consumed / bookHours) * 100 : 0;
        let status;
        if (consumed <= 0.01) {
          status = 'Not started';
        } else if (consumed + 0.01 >= bookHours) {
          status = 'Finished';
        } else {
          status = 'In progress';
        }

        const row = document.createElement('div');
        row.className = 'book-row';

        row.innerHTML = `
          <div class="book-header">
            <div class="book-title">${book.title}</div>
            <div class="book-meta">
              ${consumed.toFixed(1)} / ${bookHours.toFixed(1)} h • ${status}
            </div>
          </div>
          <div class="book-progress-outer">
            <div class="book-progress-inner"
                 style="width: ${Math.min(100, Math.max(0, percent)).toFixed(1)}%;"></div>
          </div>
        `;

        container.appendChild(row);
      }
    }

    function updateStatsUI() {
      const stats = computeStats();

      if (subtitleEl) {
        subtitleEl.textContent =
          `${state.config.dailyGoal.toFixed(2)} h/day • Full Cosmere (~${state.config.totalHours.toFixed(1)} h)`;
      }

      statTotalHours.textContent = stats.totalHours.toFixed(1) + ' h';
      statTotalDays.textContent = `${stats.daysWithToday} days since start`;

      statGoalCompare.textContent =
        stats.totalHours.toFixed(1) + ' h read vs ' +
        stats.expectedHours.toFixed(1) + ' h goal';

      if (stats.aheadBehind > 0.25) {
        statAheadBehind.textContent =
          `You are ahead by ${stats.aheadBehind.toFixed(1)} h.`;
      } else if (stats.aheadBehind < -0.25) {
        statAheadBehind.textContent =
          `You are behind by ${Math.abs(stats.aheadBehind).toFixed(1)} h.`;
      } else {
        statAheadBehind.textContent = `You are basically on pace.`;
      }

      statPercent.textContent = stats.percent.toFixed(1) + '%';
      progressInner.style.width = stats.percent.toFixed(1) + '%';

      renderBookProgress(stats.totalHours);

      if (stats.percent >= 100) {
        statusPill.style.display = 'inline-flex';
        statusPill.className = 'status-pill status-ahead';
        statusPill.textContent = '🎉 Cosmere complete! You did it.';
      } else if (stats.aheadBehind > 0.25) {
        statusPill.style.display = 'inline-flex';
        statusPill.className = 'status-pill status-ahead';
        statusPill.textContent = '✅ Ahead of schedule – nice!';
      } else if (stats.aheadBehind < -0.25) {
        statusPill.style.display = 'inline-flex';
        statusPill.className = 'status-pill status-behind';
        statusPill.textContent = '⏳ Slightly behind – one long session will catch you up.';
      } else {
        statusPill.style.display = 'inline-flex';
        statusPill.className = 'status-pill status-ontrack';
        statusPill.textContent =
          `📈 On track with your ${state.config.dailyGoal.toFixed(2)} h/day plan.`;
      }

      const todayKey = getTodayISO();
      const todayMinutes = state.logs[todayKey] || 0;
      if (todayMinutes > 0) {
        todayInfo.textContent = `Today: ${todayMinutes} min logged.`;
      } else {
        todayInfo.textContent = 'No reading logged yet for today.';
      }
    }

    function updateLogTable() {
      const entries = Object.entries(state.logs)
        .map(([date, minutes]) => ({ date, minutes }))
        .sort((a, b) => a.date.localeCompare(b.date));

      if (entries.length === 0) {
        emptyLogMsg.style.display = 'block';
        logTable.style.display = 'none';
        logTableBody.innerHTML = '';
        return;
      }

      emptyLogMsg.style.display = 'none';
      logTable.style.display = 'table';

      let cumulativeMinutes = 0;
      logTableBody.innerHTML = '';

      for (const entry of entries) {
        cumulativeMinutes += entry.minutes;
        const tr = document.createElement('tr');

        const dateTd = document.createElement('td');
        dateTd.textContent = entry.date;

        const minTd = document.createElement('td');
        minTd.textContent = entry.minutes + ' min';

        const cumTd = document.createElement('td');
        cumTd.textContent = (cumulativeMinutes / 60).toFixed(1) + ' h';

        tr.appendChild(dateTd);
        tr.appendChild(minTd);
        tr.appendChild(cumTd);

        logTableBody.appendChild(tr);
      }
    }

    function updateAll() {
      updateStatsUI();
      updateLogTable();
    }

    document.getElementById('saveConfigBtn').addEventListener('click', () => {
      const newStart = startDateInput.value || state.config.startDate || DEFAULT_START_DATE;
      const newTotalHours = parseFloat(totalHoursInput.value) || state.config.totalHours || DEFAULT_TOTAL_HOURS;
      const newDailyGoal = parseFloat(dailyGoalInput.value) || state.config.dailyGoal || DEFAULT_DAILY_GOAL;

      state.config.startDate = newStart;
      state.config.totalHours = newTotalHours;
      state.config.dailyGoal = newDailyGoal;
      saveState(state);
      updateAll();
      alert('Settings saved.');
    });

    document.getElementById('resetAllBtn').addEventListener('click', () => {
      if (!confirm('Reset ALL data? This clears logs and settings.')) return;
      state = {
        config: {
          startDate: DEFAULT_START_DATE,
          totalHours: DEFAULT_TOTAL_HOURS,
          dailyGoal: DEFAULT_DAILY_GOAL
        },
        logs: {}
      };
      saveState(state);
      initUI();
      alert('All data cleared.');
    });

    document.getElementById('logTodayBtn').addEventListener('click', () => {
      const minutes = parseInt(todayMinutesInput.value, 10);
      const todayKey = getTodayISO();

      if (isNaN(minutes) || minutes <= 0) {
        alert('Enter a positive number of minutes.');
        return;
      }

      state.logs[todayKey] = (state.logs[todayKey] || 0) + minutes;
      saveState(state);

      todayMinutesInput.value = '';
      updateAll();
    });

    document.getElementById('clearTodayBtn').addEventListener('click', () => {
      const todayKey = getTodayISO();
      if (state.logs[todayKey] != null) {
        delete state.logs[todayKey];
        saveState(state);
        todayMinutesInput.value = '';
        updateAll();
      }
    });

    // Init
    initUI();
  </script>
</body>
</html>
