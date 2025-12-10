<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>sunerasapumal — GitHub Profile / Dark Dashboard</title>
  <meta name="description" content="Dark-themed interactive GitHub profile / professional dashboard for sunerasapumal" />
  <style>
    :root{
      --bg:#0b0f14;
      --card:#0f1720;
      --muted:#9aa4b2;
      --accent:#6ee7b7;
      --glass: rgba(255,255,255,0.03);
      --glass-2: rgba(255,255,255,0.02);
      --glow: 0 6px 30px rgba(110,231,183,0.06);
      color-scheme: dark;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:radial-gradient(1200px 600px at 10% 10%, rgba(102,126,234,0.08), transparent), radial-gradient(900px 500px at 90% 90%, rgba(124,58,237,0.06), transparent), var(--bg); color:#e6eef6}

    /* page layout */
    .wrap{max-width:1100px;margin:40px auto;padding:28px;display:grid;grid-template-columns:360px 1fr;gap:28px}

    /* left column */
    .profile-card{background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);border-radius:16px;padding:22px;box-shadow:var(--glow);position:relative;overflow:hidden}
    .avatar{width:110px;height:110px;border-radius:50%;border:3px solid rgba(255,255,255,0.06);overflow:hidden}
    .avatar img{width:100%;height:100%;object-fit:cover;display:block}
    .name{font-size:20px;font-weight:700;margin-top:10px}
    .handle{color:var(--muted);font-size:13px}
    .bio{margin-top:12px;color:var(--muted);line-height:1.45}

    .labels{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
    .label{background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:6px 10px;border-radius:999px;font-size:12px;color:var(--muted);border:1px solid rgba(255,255,255,0.02)}

    .stats{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:14px}
    .stat{background:var(--glass);padding:10px;border-radius:10px;text-align:center}
    .stat .n{font-weight:700}
    .stat .t{font-size:12px;color:var(--muted)}

    /* stickers (floating) */
    .stickers{position:absolute;inset:0;pointer-events:none}
    .sticker{position:absolute;font-size:24px;opacity:0.98;transform-origin:center}
    .s1{left:18px;top:-8px;animation:float 6s ease-in-out infinite}
    .s2{right:18px;top:24%;animation:float 7.2s ease-in-out infinite}
    .s3{left:50%;bottom:-12px;transform:translateX(-50%);animation:float 5.4s ease-in-out infinite}
    .s4{right:6px;bottom:6px;animation:float 6.8s ease-in-out infinite}
    @keyframes float{0%{transform:translateY(0) rotate(0)}50%{transform:translateY(-10px) rotate(8deg)}100%{transform:translateY(0) rotate(0)}}

    /* right column */
    .panel{background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);padding:20px;border-radius:14px;box-shadow:var(--glow)}
    .grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}

    .card{background:var(--card);padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,0.02)}
    .card h3{margin:0 0 8px 0;font-size:14px}
    .projs{display:flex;flex-direction:column;gap:10px}
    .proj{display:flex;gap:12px;align-items:center}
    .proj .dot{width:46px;height:46;border-radius:8px;background:linear-gradient(135deg,rgba(255,255,255,0.02),transparent);display:flex;align-items:center;justify-content:center;font-size:18px}
    .proj .meta{flex:1}
    .proj .meta h4{margin:0;font-size:13px}
    .proj .meta p{margin:4px 0 0 0;color:var(--muted);font-size:12px}

    /* skills */
    .skill{margin-bottom:8px}
    .skill .row{display:flex;justify-content:space-between;font-size:13px}
    .bar{height:8px;background:var(--glass-2);border-radius:6px;margin-top:6px;overflow:hidden}
    .bar > i{display:block;height:100%;background:linear-gradient(90deg,var(--accent),#60a5fa);width:0%;transition:width 1.2s cubic-bezier(.2,.9,.3,1)}

    /* terminal */
    .terminal{background:#05080a;border-radius:8px;padding:14px;color:#cfeef0;font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", "Courier New", monospace;font-size:13px}
    .terminal .line{opacity:0.95}

    /* animated chart (svg) */
    .spark{width:100%;height:60px}

    /* footer */
    .footer{display:flex;gap:12px;align-items:center;margin-top:18px}
    .btn{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px 12px;border-radius:8px;font-size:13px;color:var(--muted);text-decoration:none}

    /* small screens */
    @media (max-width:900px){.wrap{grid-template-columns:1fr;padding:18px}.profile-card{order:2}.panel{order:1}}

  </style>
</head>
<body>
  <div class="wrap" id="app">
    <div class="profile-card">
      <div style="display:flex;gap:14px;align-items:center">
        <div class="avatar"><img src="https://github.com/sunerasapumal.png" alt="avatar" /></div>
        <div>
          <div class="name">Sunera Sapumal</div>
          <div class="handle">@sunerasapumal · Software Engineer • Web Dev • IoT</div>
          <div class="bio">Creative dev focused on building polished web apps, developer tools and clothing brand side-projects. „Be Bold, Be Eminent."</div>
        </div>
      </div>

      <div class="labels">
        <div class="label">Java • Spring Boot</div>
        <div class="label">React • Tailwind</div>
        <div class="label">Node • Express</div>
        <div class="label">Product & Design</div>
      </div>

      <div class="stats">
        <div class="stat"><div class="n" id="reposCount">—</div><div class="t">Repos</div></div>
        <div class="stat"><div class="n" id="followers">—</div><div class="t">Followers</div></div>
        <div class="stat"><div class="n" id="stars">—</div><div class="t">Stars</div></div>
      </div>

      <div class="footer" style="margin-top:12px">
        <a class="btn" href="https://github.com/sunerasapumal" target="_blank">View GitHub</a>
        <a class="btn" href="mailto:sunera@example.com">Email</a>
        <a class="btn" href="#contact">Contact</a>
      </div>

      <div class="stickers" aria-hidden>
        <div class="sticker s1">🚀</div>
        <div class="sticker s2">🎧</div>
        <div class="sticker s3">👕</div>
        <div class="sticker s4">✨</div>
      </div>
    </div>

    <div class="panel">
      <div style="display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:10px">
        <h2 style="margin:0">Developer Dashboard</h2>
        <div style="font-size:13px;color:var(--muted)">Dark • Interactive • Animated</div>
      </div>

      <div class="grid">
        <div class="card">
          <h3>Top Projects</h3>
          <div class="projs" id="projectList">
            <!-- filled by JS -->
          </div>
        </div>

        <div class="card">
          <h3>Skills</h3>
          <div class="skill"><div class="row"><span>Java</span><span>85%</span></div><div class="bar"><i data-w="85"></i></div></div>
          <div class="skill"><div class="row"><span>Spring Boot</span><span>78%</span></div><div class="bar"><i data-w="78"></i></div></div>
          <div class="skill"><div class="row"><span>Web / JS</span><span>82%</span></div><div class="bar"><i data-w="82"></i></div></div>
          <div class="skill"><div class="row"><span>UI / Design</span><span>70%</span></div><div class="bar"><i data-w="70"></i></div></div>
        </div>

        <div class="card">
          <h3>Live Terminal</h3>
          <div class="terminal" id="terminal">
            <div class="line">$ welcome — fetching recent activity...</div>
            <div class="line" id="termLines"></div>
          </div>
        </div>

        <div class="card">
          <h3>Monthly Activity</h3>
          <!-- simple animated sparkline -->
          <svg class="spark" viewBox="0 0 200 60" preserveAspectRatio="none" id="sparkSVG">
            <path d="" fill="none" stroke="url(#g)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"></path>
            <defs>
              <linearGradient id="g"><stop offset="0%" stop-color="#6ee7b7" stop-opacity="0.9"/><stop offset="100%" stop-color="#60a5fa" stop-opacity="0.9"/></linearGradient>
            </defs>
          </svg>
        </div>
      </div>

      <div style="margin-top:14px;display:flex;gap:12px;flex-wrap:wrap;align-items:center">
        <a class="btn" href="https://github.com/sunerasapumal?tab=repositories" target="_blank">All Repos</a>
        <a class="btn" href="https://twitter.com/intent/tweet?text=Check%20out%20sunerasapumal%20on%20GitHub!" target="_blank">Share</a>
        <a class="btn" href="#contact">Hire / Collaborate</a>
      </div>

      <div id="contact" style="margin-top:16px;padding-top:14px;border-top:1px dashed rgba(255,255,255,0.02);">
        <h3 style="margin-top:6px">Contact & Links</h3>
        <div style="display:flex;gap:8px;align-items:center;flex-wrap:wrap;margin-top:8px">
          <a class="btn" href="https://www.linkedin.com/in/sunerasapumal" target="_blank">LinkedIn</a>
          <a class="btn" href="https://instagram.com/sunerasapumal" target="_blank">Instagram</a>
          <a class="btn" href="https://t.me/sunerasapumal" target="_blank">Telegram</a>
        </div>
      </div>

    </div>
  </div>

  <script>
    /* --- small helper: fetch public user data and repos --- */
    const username = 'sunerasapumal';

    async function fetchGitData(){
      try{
        const userRes = await fetch('https://api.github.com/users/' + username);
        if(!userRes.ok) throw new Error('user fetch failed');
        const user = await userRes.json();
        document.getElementById('reposCount').textContent = user.public_repos;
        document.getElementById('followers').textContent = user.followers;

        // stars: sum of stargazers_count across top repos
        const reposRes = await fetch('https://api.github.com/users/' + username + '/repos?per_page=100&sort=updated');
        const repos = await reposRes.json();
        let stars = 0;
        repos.forEach(r => stars += r.stargazers_count || 0);
        document.getElementById('stars').textContent = stars;

        // top 4 projects
        const sorted = repos.sort((a,b)=> (b.stargazers_count - a.stargazers_count)).slice(0,6);
        const projNode = document.getElementById('projectList');
        projNode.innerHTML = '';
        sorted.forEach(p=>{
          const div = document.createElement('div'); div.className='proj';
          div.innerHTML = `<div class="dot">${p.name[0].toUpperCase()}</div><div class="meta"><h4><a style="color:inherit;text-decoration:none" href="${p.html_url}" target="_blank">${p.name}</a></h4><p>${(p.description||'No description').slice(0,80)}</p></div>`;
          projNode.appendChild(div);
        });

        // terminal lines: recent commits (mock using repo names and updated_at)
        const term = document.getElementById('termLines');
        term.innerHTML = '';
        const recent = repos.slice(0,6);
        recent.forEach(r =>{
          const d = new Date(r.updated_at).toLocaleString();
          const l = document.createElement('div'); l.className='line'; l.textContent = `$ git pull ${r.name} — updated: ${d}`; term.appendChild(l);
        });

        // sparkline values: contributions-like data from pushed_at dates
        const points = repos.slice(0,10).map((r,i)=> Math.min(50, Math.abs(new Date() - new Date(r.pushed_at))/1000/60/60/24 % 50 + (i*3)));
        drawSpark(points);

        // animate skill bars
        document.querySelectorAll('.bar > i').forEach(el=>{
          const w = el.getAttribute('data-w') || '40';
          setTimeout(()=> el.style.width = w + '%', 300);
        });

      }catch(err){
        console.warn(err);
      }
    }

    function drawSpark(arr){
      if(!arr || !arr.length) return;
      const w = 200, h = 60;
      const step = w / (arr.length - 1);
      const max = Math.max(...arr);
      const min = Math.min(...arr);
      const pts = arr.map((v,i)=> `${i*step},${h - ((v - min)/(max - min || 1) * (h-10) + 5)}`);
      const path = document.querySelector('#sparkSVG path');
      path.setAttribute('d', 'M' + pts.join(' L '));

      // animate stroke-dashoffset
      const length = path.getTotalLength();
      path.style.strokeDasharray = length;
      path.style.strokeDashoffset = length;
      path.getBoundingClientRect();
      path.style.transition = 'stroke-dashoffset 1.2s ease-out';
      path.style.strokeDashoffset = '0';
    }

    fetchGitData();

    // little entrance animations
    document.addEventListener('DOMContentLoaded', ()=>{
      document.querySelectorAll('.card').forEach((c,i)=>{c.style.transform='translateY(8px)';c.style.opacity=0;setTimeout(()=>{c.style.transition='all 420ms cubic-bezier(.2,.9,.3,1)';c.style.transform='translateY(0)';c.style.opacity=1;}, 120*i)});
    });

    // optional: make SVG stickers clickable to change theme (demo)
    document.querySelectorAll('.sticker').forEach(s=> s.addEventListener('click', ()=> alert('Hi! Want this customised?')));
  </script>

</body>
</html>
