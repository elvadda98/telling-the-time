<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Tell the Time — Speaking Practice</title>
  <style>
    :root{
      --bg1:#0b1220;
      --bg2:#0f2a3a;
      --card:#0f1b2b;
      --muted:#9fb3c8;
      --text:#eaf2ff;
      --accent:#64d404;
      --accent2:#5ad7ff;
      --bad:#ff5a7a;
      --good:#64d404;
      --shadow: 0 14px 40px rgba(0,0,0,.35);
      --radius: 20px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      color:var(--text);
      background:
        radial-gradient(1200px 700px at 15% 10%, rgba(90,215,255,.22), transparent 55%),
        radial-gradient(900px 600px at 85% 25%, rgba(100,212,4,.18), transparent 60%),
        linear-gradient(160deg, var(--bg1), var(--bg2));
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:18px;
    }
    .wrap{width:min(980px, 100%);}
    .topbar{
      display:flex;
      gap:12px;
      align-items:center;
      justify-content:space-between;
      margin-bottom:14px;
    }
    .badge{
      background:rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.12);
      padding:10px 12px;
      border-radius:999px;
      color:var(--muted);
      font-size:14px;
      display:flex;
      gap:10px;
      align-items:center;
    }
    .pill{
      display:inline-flex;
      align-items:center;
      gap:8px;
      padding:9px 12px;
      border-radius:999px;
      background:rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.12);
      color:var(--muted);
      font-size:14px;
      cursor:pointer;
      user-select:none;
    }
    .pill:active{transform:translateY(1px)}
    .grid{
      display:grid;
      grid-template-columns: 1.05fr .95fr;
      gap:16px;
    }
    @media (max-width: 860px){
      .grid{grid-template-columns:1fr}
    }
    .card{
      background:rgba(15,27,43,.82);
      border:1px solid rgba(255,255,255,.10);
      border-radius:var(--radius);
      box-shadow: var(--shadow);
      overflow:hidden;
    }
    .card h2{
      margin:0;
      padding:16px 18px 0 18px;
      font-size:18px;
      letter-spacing:.2px;
    }
    .sub{
      margin:6px 0 0 0;
      padding:0 18px 14px 18px;
      color:var(--muted);
      font-size:14px;
      line-height:1.35;
    }
    .main{
      padding:18px;
      display:flex;
      flex-direction:column;
      gap:14px;
    }
    .timeBox{
      border-radius:18px;
      border:1px solid rgba(255,255,255,.14);
      background:
        radial-gradient(800px 220px at 10% 0%, rgba(100,212,4,.12), transparent 55%),
        radial-gradient(700px 260px at 90% 20%, rgba(90,215,255,.16), transparent 60%),
        rgba(255,255,255,.04);
      padding:18px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
    }
    .digital{
      font-variant-numeric: tabular-nums;
      font-size:54px;
      font-weight:800;
      letter-spacing:1.5px;
    }
    .hint{
      color:var(--muted);
      font-size:13px;
      line-height:1.3;
      text-align:right;
      max-width:300px;
    }
    .actions{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      align-items:center;
    }
    button{
      border:0;
      border-radius:16px;
      padding:12px 14px;
      font-weight:700;
      cursor:pointer;
      background:rgba(255,255,255,.08);
      color:var(--text);
      border:1px solid rgba(255,255,255,.14);
      transition: .15s transform, .15s filter, .15s background;
    }
    button:hover{filter:brightness(1.06)}
    button:active{transform:translateY(1px)}
    .primary{
      background: linear-gradient(90deg, rgba(100,212,4,.95), rgba(90,215,255,.55));
      border:1px solid rgba(255,255,255,.16);
      color:#071014;
    }
    .danger{
      background: rgba(255,90,122,.12);
      border: 1px solid rgba(255,90,122,.35);
    }
    .row{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      align-items:center;
      width:100%;
    }
    input[type="text"]{
      flex:1;
      min-width:240px;
      padding:12px 14px;
      border-radius:16px;
      background:rgba(0,0,0,.18);
      border:1px solid rgba(255,255,255,.14);
      color:var(--text);
      outline:none;
    }
    input[type="text"]::placeholder{color:rgba(159,179,200,.75)}
    .status{
      padding:12px 14px;
      border-radius:16px;
      border:1px solid rgba(255,255,255,.12);
      background:rgba(255,255,255,.05);
      color:var(--muted);
      line-height:1.35;
    }
    .status.good{border-color: rgba(100,212,4,.55); color: #dfffe0; background: rgba(100,212,4,.10)}
    .status.bad{border-color: rgba(255,90,122,.55); color: #ffe2e9; background: rgba(255,90,122,.10)}
    .side{
      padding:18px;
      display:flex;
      flex-direction:column;
      gap:12px;
    }
    .mini{
      padding:14px;
      border-radius:18px;
      border:1px solid rgba(255,255,255,.10);
      background:rgba(255,255,255,.04);
    }
    .mini h3{
      margin:0 0 6px 0;
      font-size:15px;
    }
    ul{
      margin:8px 0 0 18px;
      color:var(--muted);
      line-height:1.45;
      font-size:14px;
    }
    .kv{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      color:var(--muted);
      font-size:14px;
    }
    .k{
      padding:8px 10px;
      border-radius:999px;
      background:rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.10);
    }
    .footerNote{
      color:rgba(159,179,200,.85);
      font-size:12.5px;
      line-height:1.35;
    }
    .small{
      font-size:12px;
      color:rgba(159,179,200,.85);
    }
    .mono{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      font-size: 12.5px;
      color: rgba(234,242,255,.92);
      background: rgba(0,0,0,.18);
      border: 1px solid rgba(255,255,255,.10);
      padding: 10px 12px;
      border-radius: 14px;
      white-space: pre-wrap;
      word-break: break-word;
    }
  </style>
</head>
<body>
  <div class="wrap">
    <div class="topbar">
      <div class="badge">
        <strong style="color:var(--text); font-weight:800;">Tell the Time</strong>
        <span>Speak the time you see</span>
      </div>
      <div style="display:flex; gap:10px; align-items:center;">
        <div class="badge" title="Correct answers">
          ✅ Score: <span id="score" style="color:var(--text); font-weight:800;">0</span>
        </div>
        <div class="pill" id="toggleHelp" title="Show/Hide acceptable answers">👀 Show answers</div>
      </div>
    </div>

    <div class="grid">
      <div class="card">
        <h2>Exercise</h2>
        <p class="sub">
          Read the digital time out loud using: <b>o'clock</b>, <b>past</b>, <b>half past</b>, or <b>to</b> (5/10/quarter/20/25).
          If your pronunciation is recognized correctly, a new time appears.
        </p>

        <div class="main">
          <div class="timeBox">
            <div>
              <div class="small">Digital time</div>
              <div class="digital" id="digital">--:--</div>
            </div>
            <div class="hint" id="hint">
              Press <b>🎤 Start</b> and say the time.<br/>
              Example: <i>quarter past three</i>, <i>twenty to seven</i>, <i>five o'clock</i>.
            </div>
          </div>

          <div class="actions">
            <button class="primary" id="startBtn">🎤 Start</button>
            <button id="stopBtn" disabled>⏹ Stop</button>
            <button id="newBtn">🔄 New time</button>
            <button class="danger" id="skipBtn">⏭ I can’t / skip</button>
          </div>

          <div class="row">
            <input id="manual" type="text" placeholder="No microphone? Type what you would say (e.g., 'quarter to six') and press Check" />
            <button id="checkBtn">✅ Check</button>
          </div>

          <div id="status" class="status">Ready. Click 🎤 Start and speak clearly.</div>

          <div id="answersBox" class="mini" style="display:none;">
            <h3>Accepted answers for this time</h3>
            <div class="mono" id="answersText">—</div>
            <div class="footerNote" style="margin-top:8px;">
              Tip: small variations are fine (e.g., “it’s …”, “a quarter past …”, hyphens).
            </div>
          </div>
        </div>
      </div>

      <div class="card">
        <div class="side">
          <div class="mini">
            <h3>Forms you’ll practice</h3>
            <div class="kv">
              <span class="k">o'clock</span>
              <span class="k">five past</span>
              <span class="k">ten past</span>
              <span class="k">quarter past</span>
              <span class="k">twenty past</span>
              <span class="k">twenty-five past</span>
              <span class="k">half past</span>
              <span class="k">five to</span>
              <span class="k">ten to</span>
              <span class="k">quarter to</span>
              <span class="k">twenty to</span>
              <span class="k">twenty-five to</span>
            </div>
          </div>

          <div class="mini">
            <h3>Quick tips</h3>
            <ul>
              <li><b>15</b> minutes = <b>quarter</b>.</li>
              <li><b>30</b> minutes = <b>half past</b>.</li>
              <li>When it’s <b>to</b>, you use the <b>next hour</b> (e.g., 6:40 = <i>twenty to seven</i>).</li>
              <li>Speak slowly: <i>quarter to six</i> (not “quater”).</li>
            </ul>
          </div>

          <div class="mini">
            <h3>Browser note</h3>
            <p class="footerNote" style="margin:0;">
              Speech recognition works best in Chrome/Edge. If it’s not available, use the typing box and press <b>Check</b>.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    // ===== Utilities =====
    const HOUR_WORD = {
      1:"one",2:"two",3:"three",4:"four",5:"five",6:"six",
      7:"seven",8:"eight",9:"nine",10:"ten",11:"eleven",12:"twelve"
    };
    const MIN_WORD = {
      0:"o'clock",
      5:"five",
      10:"ten",
      15:"quarter",
      20:"twenty",
      25:"twenty five",
      30:"half"
    };

    function pad2(n){ return String(n).padStart(2,"0"); }

    function normalize(s){
      return (s || "")
        .toLowerCase()
        .replace(/’|'/g,"")
        .replace(/-/g," ")
        .replace(/[^\w\s]/g," ")
        .replace(/\s+/g," ")
        .trim();
    }

    function stripIntro(s){
      // remove common prefixes
      s = normalize(s);
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^it\s+is\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^its\s+/,"");
      // (yes, that looks silly, but harmless—kept simple & standalone)
      s = s.replace(/^its\s+/,"");
      s = s.replace(/^it\s+s\s+/,""); // "it's" -> often becomes "it s"
      s = s.replace(/^it\s+s\s+/,"");
      s = s.replace(/^it\s+s\s+/,"");
      s = s.replace(/^it\s+s\s+/,"");
      return s.trim();
    }

    function unique(arr){
      const seen = new Set();
      const out = [];
      for(const x of arr){
        const n = normalize(x);
        if(!n) continue;
        if(!seen.has(n)){
          seen.add(n);
          out.push(x);
        }
      }
      return out;
    }

    // ===== Time generation based on requested forms =====
    const ALLOWED_MINUTES = [0,5,10,15,20,25,30,35,40,45,50,55];

    function randomInt(min, max){ // inclusive
      return Math.floor(Math.random()*(max-min+1))+min;
    }

    function pickNewTime(){
      const hour = randomInt(1,12);
      const minute = ALLOWED_MINUTES[randomInt(0, ALLOWED_MINUTES.length-1)];
      return {hour, minute};
    }

    function buildAcceptedPhrases(hour, minute){
      // Returns an array of acceptable spoken phrases.
      // For minutes > 30, we use "to" with next hour.
      const phrases = [];
      const hourWord = HOUR_WORD[hour];

      const addCommonIntros = (core) => {
        // allow optional intros
        phrases.push(core);
        phrases.push("its " + core);      // "it's" often transcribed as "its"
        phrases.push("it is " + core);
        phrases.push("it's " + core);
      };

      if(minute === 0){
        const core1 = `${hourWord} o'clock`;
        addCommonIntros(core1);
        // allow missing apostrophe or even just hour word (some recognizers drop "o'clock")
        addCommonIntros(`${hourWord} oclock`);
        addCommonIntros(`${hourWord}`);
        return unique(phrases);
      }

      if(minute === 30){
        const core = `half past ${hourWord}`;
        addCommonIntros(core);
        // optional "a"
        addCommonIntros(`a half past ${hourWord}`); // uncommon but harmless
        return unique(phrases);
      }

      if(minute < 30){
        const m = minute;
        const mw = MIN_WORD[m];
        const core = `${mw} past ${hourWord}`;
        addCommonIntros(core);

        // quarter variations
        if(m === 15){
          addCommonIntros(`a quarter past ${hourWord}`);
          addCommonIntros(`quarter past ${hourWord}`);
        } else {
          addCommonIntros(`${mw} minutes past ${hourWord}`);
        }

        // hyphen variation for twenty-five
        if(m === 25){
          addCommonIntros(`twenty-five past ${hourWord}`);
          addCommonIntros(`twenty-five minutes past ${hourWord}`);
        }
        return unique(phrases);
      }

      // minute > 30 => "to"
      const nextHour = (hour % 12) + 1;
      const nextHourWord = HOUR_WORD[nextHour];
      const remaining = 60 - minute; // 55=>5, 50=>10, 45=>15, 40=>20, 35=>25
      const rw = (remaining === 25) ? "twenty five" : MIN_WORD[remaining];
      const core = `${rw} to ${nextHourWord}`;
      addCommonIntros(core);

      if(remaining === 15){
        addCommonIntros(`a quarter to ${nextHourWord}`);
        addCommonIntros(`quarter to ${nextHourWord}`);
      } else {
        addCommonIntros(`${rw} minutes to ${nextHourWord}`);
      }

      if(remaining === 25){
        addCommonIntros(`twenty-five to ${nextHourWord}`);
        addCommonIntros(`twenty-five minutes to ${nextHourWord}`);
      }
      return unique(phrases);
    }

    function toDigital(hour, minute){
      // show as 12-hour digital: H:MM
      return `${hour}:${pad2(minute)}`;
    }

    // ===== Speech Recognition =====
    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    let recog = null;
    let listening = false;

    function canUseSpeech(){
      return !!SpeechRecognition;
    }

    function makeRecognizer(){
      const r = new SpeechRecognition();
      r.lang = "en-GB"; // native-ish
      r.interimResults = false;
      r.maxAlternatives = 3;
      r.continuous = false;

      r.onstart = () => {
        listening = true;
        startBtn.disabled = true;
        stopBtn.disabled = false;
        setStatus("Listening… Speak now.", "status");
      };

      r.onend = () => {
        listening = false;
        startBtn.disabled = false;
        stopBtn.disabled = true;
        if(!lastHeard){
          setStatus("Stopped. Click 🎤 Start to try again.", "status");
        }
      };

      r.onerror = (e) => {
        listening = false;
        startBtn.disabled = false;
        stopBtn.disabled = true;
        setStatus(`Speech error: ${e.error}. You can use the typing box instead.`, "bad");
      };

      r.onresult = (evt) => {
        const res = evt.results?.[0];
        const transcript = res?.[0]?.transcript || "";
        lastHeard = transcript;
        handleAttempt(transcript);
      };

      return r;
    }

    // ===== Game state =====
    const digitalEl = document.getElementById("digital");
    const statusEl = document.getElementById("status");
    const scoreEl = document.getElementById("score");
    const answersBox = document.getElementById("answersBox");
    const answersText = document.getElementById("answersText");

    const startBtn = document.getElementById("startBtn");
    const stopBtn  = document.getElementById("stopBtn");
    const newBtn   = document.getElementById("newBtn");
    const skipBtn  = document.getElementById("skipBtn");
    const manualIn = document.getElementById("manual");
    const checkBtn = document.getElementById("checkBtn");
    const toggleHelp = document.getElementById("toggleHelp");

    let current = pickNewTime();
    let accepted = buildAcceptedPhrases(current.hour, current.minute);
    let score = 0;
    let lastHeard = "";

    function setStatus(msg, kind){
      statusEl.textContent = msg;
      statusEl.className = "status";
      if(kind === "good") statusEl.classList.add("good");
      if(kind === "bad")  statusEl.classList.add("bad");
    }

    function render(){
      digitalEl.textContent = toDigital(current.hour, current.minute);
      accepted = buildAcceptedPhrases(current.hour, current.minute);

      const show = answersBox.style.display !== "none";
      if(show){
        answersText.textContent = accepted.join("\n");
      }
    }

    function nextTime(){
      current = pickNewTime();
      lastHeard = "";
      manualIn.value = "";
      setStatus("New time! Click 🎤 Start and speak.", "status");
      render();
    }

    function isCorrectAttempt(raw){
      const attempt = stripIntro(raw);
      const nAttempt = normalize(attempt);

      // Compare against normalized variants.
      const normalizedVariants = accepted.map(a => normalize(stripIntro(a)));

      // Accept if attempt contains a full variant or equals it.
      for(const v of normalizedVariants){
        if(!v) continue;
        if(nAttempt === v) return true;
        if(nAttempt.includes(v)) return true;
      }

      // Extra forgiveness: allow "twenty five" vs "twenty five" already handled;
      // allow "oclock" vs "o'clock" already handled.
      return false;
    }

    function handleAttempt(raw){
      const ok = isCorrectAttempt(raw);
      if(ok){
        score += 1;
        scoreEl.textContent = String(score);
        setStatus(`✅ Correct! I heard: “${raw}”. New time…`, "good");
        setTimeout(nextTime, 650);
      }else{
        setStatus(`❌ Not quite. I heard: “${raw}”. Try again (or click “Show answers”).`, "bad");
      }
    }

    // ===== Wire up UI =====
    startBtn.addEventListener("click", () => {
      lastHeard = "";
      if(!canUseSpeech()){
        setStatus("Speech recognition not supported in this browser. Use the typing box and press Check.", "bad");
        return;
      }
      if(!recog) recog = makeRecognizer();
      try{
        recog.start();
      }catch(e){
        // If start is called too quickly twice, it can throw.
        setStatus("Couldn’t start the microphone. If it keeps happening, use the typing box.", "bad");
      }
    });

    stopBtn.addEventListener("click", () => {
      if(recog && listening){
        try{ recog.stop(); }catch(e){}
      }
    });

    newBtn.addEventListener("click", nextTime);

    skipBtn.addEventListener("click", () => {
      setStatus("Skipped. New time…", "status");
      setTimeout(nextTime, 250);
    });

    checkBtn.addEventListener("click", () => {
      const typed = manualIn.value.trim();
      if(!typed){
        setStatus("Type what you would say, then press Check.", "bad");
        return;
      }
      handleAttempt(typed);
    });

    manualIn.addEventListener("keydown", (e) => {
      if(e.key === "Enter") checkBtn.click();
    });

    toggleHelp.addEventListener("click", () => {
      const isHidden = answersBox.style.display === "none";
      answersBox.style.display = isHidden ? "block" : "none";
      toggleHelp.textContent = isHidden ? "🙈 Hide answers" : "👀 Show answers";
      if(isHidden){
        answersText.textContent = accepted.join("\n");
      }
    });

    // Init
    render();
    if(!canUseSpeech()){
      setStatus("Speech recognition not available here. Use the typing box and press Check.", "bad");
      startBtn.disabled = true;
      startBtn.textContent = "🎤 Start (not supported)";
    }
  </script>
</body>
</html>
