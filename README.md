<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Quest2Play — Submit & Earn (3 pts each)</title>
<style>
  :root{
    --accent:#7c5cff; --accent2:#ffb86b; --muted:#cbd5e1; --glass:rgba(255,255,255,0.04);
  }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,Arial;background:#030313;color:#fff}
  /* Background: game collage (direct URL) */
  body{
    background:
      linear-gradient(180deg, rgba(2,6,23,0.25), rgba(2,6,23,0.65)),
      url("https://images.wallpapersden.com/image/download/valorant-vs-mobile-legends-hd_bG1maG2UmZqaraWkpJRmbmdlrWZlbWU.jpg");
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    -webkit-font-smoothing:antialiased; -moz-osx-font-smoothing:grayscale;
  }

  /* Top navigation */
  .topbar{position:sticky;top:0;z-index:40;display:flex;align-items:center;justify-content:space-between;padding:14px 20px;background:linear-gradient(90deg, rgba(0,0,0,0.45), rgba(0,0,0,0.15))}
  .brand{display:flex;align-items:center;gap:12px}
  .logo{width:56px;height:56px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#5a41c9);display:flex;align-items:center;justify-content:center;font-weight:800}
  nav a{color:var(--muted);text-decoration:none;margin:0 10px;padding:8px 10px;border-radius:8px}
  nav a:hover{background:rgba(255,255,255,0.03);color:#fff}

  /* container and cards */
  .wrap{max-width:1200px;margin:26px auto;padding:18px}
  .card{background:var(--glass);padding:18px;border-radius:12px;margin-bottom:18px;backdrop-filter: blur(6px)}
  h1{margin:0;font-size:34px}
  p.lead{color:var(--muted);margin-top:10px}

  /* layout */
  .hero{display:grid;grid-template-columns:1fr 360px;gap:18px;align-items:start;padding:24px;border-radius:12px}
  .badges{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
  .badge{padding:6px 10px;border-radius:999px;background:rgba(255,255,255,0.03);color:var(--muted);font-weight:700;font-size:13px}

  /* panel */
  .panel{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.12));padding:14px;border-radius:10px}
  .points{font-size:36px;font-weight:900}
  .muted{color:var(--muted)}

  /* upload form */
  .upload-grid{display:grid;grid-template-columns:1fr 320px;gap:16px}
  .field{display:block;margin-bottom:10px}
  .label{display:block;margin-bottom:6px;color:var(--muted);font-size:13px}
  input[type=text],select{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:#fff}
  input[type=file]{display:none}
  .filebtn{display:inline-block;padding:10px 12px;border-radius:8px;background:linear-gradient(90deg,#f97316,#ffb86b);color:#111;font-weight:800;cursor:pointer}
  .preview{width:100%;border-radius:8px;margin-top:10px;display:block}

  /* submissions list */
  .subs{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:12px;margin-top:12px}
  .sub{background:rgba(255,255,255,0.02);padding:10px;border-radius:8px}
  .sub img{width:100%;height:120px;object-fit:cover;border-radius:6px}

  /* footer */
  footer{margin-top:18px;text-align:center;color:var(--muted);padding:18px}

  /* responsive */
  @media (max-width:900px){
    .hero{grid-template-columns:1fr}
    nav{display:none}
  }
</style>
</head>
<body>
  <header class="topbar">
    <div class="brand">
      <div class="logo">Q2P</div>
      <div>
        <div style="font-weight:800">Quest2Play</div>
        <div class="muted" style="font-size:13px">Submit assignments — gain points</div>
      </div>
    </div>

    <nav>
      <a href="#home">Home</a>
      <a href="#how">How</a>
      <a href="#upload">Upload</a>
      <a href="#points">Points</a>
      <a href="#faq">FAQ</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main class="wrap">
    <!-- HERO -->
    <section id="home" class="card hero">
      <div>
        <h1>Submit assignments — +3 points each</h1>
        <p class="lead">Every correct submission (image or file) gives the student <strong>3 points</strong>. Images uploaded will display as proof. Points and submissions are saved locally for demo purposes.</p>

        <div class="badges">
          <span class="badge">CODM</span><span class="badge">Mobile Legends</span><span class="badge">Roblox</span>
          <span class="badge">Valorant</span><span class="badge">Honor of Kings</span><span class="badge">LoL</span>
        </div>

        <div style="margin-top:18px">
          <h3 style="margin:0 0 8px">Quick Steps</h3>
          <ol class="muted">
            <li>Fill student name and school ID.</li>
            <li>Choose a file (image preferred) and submit.</li>
            <li>You will automatically receive +3 points per successful submission.</li>
            <li>Points and image proof will appear below and persist in your browser.</li>
          </ol>
        </div>
      </div>

      <aside class="panel">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div class="muted">Your Points</div>
            <div class="points" id="pointsTotal">0</div>
          </div>
          <div style="text-align:right">
            <div class="muted">Submissions</div>
            <div id="subsCount" style="font-weight:800;font-size:20px">0</div>
          </div>
        </div>

        <div style="margin-top:12px" class="muted">Tip: upload an image as proof so it shows on the page.</div>
        <div style="margin-top:12px">
          <button class="filebtn" id="bgUploadBtn">Upload Background</button>
          <input type="file" id="bgInput" accept="image/*" style="display:none">
          <button class="filebtn" id="resetBgBtn" style="background:#2b2b2b;color:#fff;margin-left:8px">Reset BG</button>
        </div>
      </aside>
    </section>

    <!-- HOW -->
    <section id="how" class="card">
      <h2>How it works</h2>
      <p class="muted">This demo awards <strong>3 points</strong> for every successful submission. The system checks that a file was attached (image or document). If an image is uploaded it will show as a preview in the submissions area.</p>
    </section>

    <!-- UPLOAD -->
    <section id="upload" class="card">
      <h2>Upload Assignment (each correct submission = +3 points)</h2>

      <div class="upload-grid">
        <div>
          <form id="submitForm">
            <label class="field"><span class="label">Student Name</span><input id="studentName" type="text" placeholder="e.g. Juan dela Cruz" required></label>
            <label class="field"><span class="label">School ID</span><input id="studentId" type="text" placeholder="e.g. SCH-12345" required></label>
            <label class="field"><span class="label">Task Title</span><input id="taskTitle" type="text" placeholder="e.g. Math HW 3" required></label>
            <div style="margin-top:8px">
              <label class="label">Attach file (image preferred)</label>
              <label class="filebtn" for="fileInput">Choose File</label>
              <input id="fileInput" type="file" accept="image/*,.pdf,.doc,.docx">
              <div id="fileMeta" class="muted" style="margin-top:8px"></div>
            </div>

            <div style="margin-top:12px">
              <button class="btn" type="submit">Submit Assignment</button>
              <button type="button" class="btn filebtn" id="clearAll" style="background:#444;margin-left:8px">Clear All Data</button>
            </div>
          </form>

          <div style="margin-top:14px">
            <h3 style="margin:0 0 8px">Submissions</h3>
            <div id="subsGrid" class="subs"></div>
          </div>
        </div>

        <aside>
          <div class="panel">
            <h3 style="margin-top:0">Preview (images)</h3>
            <img id="filePreview" class="preview" style="display:none">
            <div id="previewInfo" class="muted" style="margin-top:8px"></div>
          </div>
        </aside>
      </div>
    </section>

    <!-- POINTS DETAILS -->
    <section id="points" class="card">
      <h2>Points Details</h2>
      <p class="muted">Each correct submission is worth <strong>3 points</strong>. Points are stored locally in your browser so they persist between refreshes (demo only).</p>
      <ul class="muted">
        <li>3 points per successful submission</li>
        <li>Images will display as proof in the Submissions area</li>
        <li>To reset data, use the Clear All Data button</li>
      </ul>
    </section>

    <!-- FAQ -->
    <section id="faq" class="card">
      <h2>FAQ</h2>
      <details><summary>Does every file give points?</summary><p class="muted">Yes — as long as a file is attached and you click Submit, the demo awards 3 points.</p></details>
      <details><summary>Where are files stored?</summary><p class="muted">Images used for preview are stored as data URLs in your browser's localStorage (demo only). For production, use a backend to store files securely.</p></details>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="card">
      <h2>Contact</h2>
      <p class="muted">Want this converted to a live site with server storage, authentication, and teacher verification? I can help set up Node/Express + storage and deploy it to Netlify, Vercel, or a VPS.</p>
    </section>

    <footer>
      <div class="muted">© 2025 Quest2Play — Demo. Submissions stored locally.</div>
    </footer>
  </main>

<script>
/* Demo behavior:
   - Each successful submit with a file adds exactly +3 points
   - If the file is an image, store and display a preview
   - All submissions + points saved in localStorage under 'q2p_demo'
*/

// helpers
const el = id => document.getElementById(id);
const ptsPerSubmit = 3; // exactly 3 points per submission

// data model in localStorage:
// { points: number, submissions: [ {name, id, title, filename, preview (dataURL|null), at} ] }

function loadData(){
  try{
    const raw = localStorage.getItem('q2p_demo');
    if(!raw) return { points:0, submissions:[] };
    return JSON.parse(raw);
  } catch(e) { return { points:0, submissions:[] }; }
}
function saveData(data){ localStorage.setItem('q2p_demo', JSON.stringify(data)); }

function formatDateISO(iso){ return new Date(iso).toLocaleString(); }

// render UI
function renderAll(){
  const data = loadData();
  el('pointsTotal').innerText = data.points;
  el('subsCount').innerText = data.submissions.length;
  // render submissions grid
  const grid = el('subsGrid'); grid.innerHTML = '';
  data.submissions.forEach((s, idx) => {
    const d = document.createElement('div'); d.className = 'sub';
    let imgHtml = '';
    if(s.preview){
      imgHtml = `<img src="${s.preview}" alt="preview">`;
    }
    d.innerHTML = `
      ${imgHtml}
      <div style="margin-top:8px"><strong>${escapeHtml(s.name)}</strong></div>
      <div class="muted" style="font-size:13px">${escapeHtml(s.title)} • ${escapeHtml(s.filename)}</div>
      <div class="muted" style="font-size:12px;margin-top:6px">${formatDateISO(s.at)}</div>
      <div style="margin-top:8px"><button data-idx="${idx}" class="btn" style="padding:6px 8px">Delete</button></div>
    `;
    // delete handler
    d.querySelector('button').addEventListener('click', ()=>{
      if(!confirm('Delete this submission?')) return;
      deleteSubmission(idx);
    });
    grid.appendChild(d);
  });
}

// escape
function escapeHtml(s){ return (s+'').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":"&#39;"}[c])); }

// delete
function deleteSubmission(idx){
  const data = loadData();
  const removed = data.submissions.splice(idx,1);
  // reduce points by 3 for deleted submission
  data.points = Math.max(0, data.points - ptsPerSubmit);
  saveData(data);
  renderAll();
}

// file input preview logic
const fileInput = el('fileInput');
const filePreview = el('filePreview');
const fileMeta = el('fileMeta');
let lastPickedFile = null;

fileInput.addEventListener('change', (e)=>{
  const f = e.target.files[0];
  if(!f){ lastPickedFile = null; filePreview.style.display='none'; fileMeta.innerText=''; return; }
  lastPickedFile = f;
  fileMeta.innerText = `${f.name} • ${Math.round(f.size/1024)} KB`;
  if(f.type.startsWith('image/')){
    const r = new FileReader();
    r.onload = ev => { filePreview.src = ev.target.result; filePreview.style.display = 'block'; el('previewInfo').innerText = f.name; }
    r.readAsDataURL(f);
  } else {
    filePreview.style.display = 'none'; filePreview.src = ''; el('previewInfo').innerText = 'Attached file: ' + f.name;
  }
});

// submit form: require file, then award +3 points and save preview if image
el('submitForm').addEventListener('submit', (e)=>{
  e.preventDefault();
  const name = el('studentName').value.trim();
  const sid = el('studentId').value.trim();
  const title = el('taskTitle').value.trim();
  if(!name || !sid || !title){ alert('Please fill name, school ID, and task title.'); return; }
  if(!lastPickedFile){ alert('Please choose a file to submit (image recommended).'); return; }

  const f = lastPickedFile;
  // read image if image, else proceed with null preview
  if(f.type.startsWith('image/')){
    const r = new FileReader();
    r.onload = ev => {
      const previewData = ev.target.result; // dataURL
      storeSubmission(name, sid, title, f.name, previewData);
      // reset
      el('submitForm').reset(); lastPickedFile = null; filePreview.style.display='none'; fileMeta.innerText='';
      alert('Submission saved — +3 points awarded!');
    };
    r.readAsDataURL(f);
  } else {
    storeSubmission(name, sid, title, f.name, null);
    el('submitForm').reset(); lastPickedFile = null; filePreview.style.display='none'; fileMeta.innerText='';
    alert('Submission saved — +3 points awarded!');
  }
});

// store logic
function storeSubmission(name, sid, title, filename, preview){
  const data = loadData();
  const entry = { name, sid, title, filename, preview, at: new Date().toISOString() };
  data.submissions.unshift(entry);
  // award exactly 3 points per correct submission
  // do arithmetic carefully: convert to integer and add 3 digit-by-digit (here trivial)
  const current = Number(data.points) || 0;
  const newPoints = current + ptsPerSubmit; // digit-by-digit trivial addition
  data.points = newPoints;
  saveData(data);
  renderAll();
}

// export / clear
el('clearAll').addEventListener('click', ()=>{
  if(confirm('Clear all stored submissions and reset points?')){ localStorage.removeItem('q2p_demo'); renderAll(); alert('Cleared.'); }
});
el('resetBgBtn').addEventListener('click', ()=>{
  document.body.style.backgroundImage = "linear-gradient(180deg, rgba(2,6,23,0.25), rgba(2,6,23,0.65)), url('https://images.wallpapersden.com/image/download/valorant-vs-mobile-legends-hd_bG1maG2UmZqaraWkpJRmbmdlrWZlbWU.jpg')";
});
el('bgUploadBtn').addEventListener('click', ()=> el('bgInput').click());
el('bgInput').addEventListener('change', e=>{
  const f = e.target.files[0]; if(!f) return;
  const r = new FileReader();
  r.onload = ev => {
    document.body.style.backgroundImage = `linear-gradient(180deg, rgba(2,6,23,0.25), rgba(2,6,23,0.65)), url('${ev.target.result}')`;
  };
  r.readAsDataURL(f);
});

// export JSON button (top nav export)
const topExportBtn = document.createElement('button');
topExportBtn.innerText = 'Export Data';
topExportBtn.style.display = 'none'; // we won't show top; user can use Clear / no separate export here
// provide export via keyboard: Ctrl+E for convenience
document.addEventListener('keydown', (ev)=>{ if(ev.ctrlKey && ev.key.toLowerCase()==='e'){ ev.preventDefault(); downloadJSON(); }});
function downloadJSON(){
  const raw = localStorage.getItem('q2p_demo') || '[]';
  const blob = new Blob([raw], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a'); a.href = url; a.download = 'quest2play_demo_submissions.json'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
}
el('clearAll').insertAdjacentHTML('afterend',' <button id="exportLocal" class="filebtn" style="margin-left:8px">Export JSON</button>');
el('exportLocal').addEventListener('click', downloadJSON);

// initial render
renderAll();
</script>
</body>
</html>
