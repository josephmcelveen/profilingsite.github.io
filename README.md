<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>FERIS™ | Front-End Recruiting Intelligence System</title>
  <meta name="description" content="AI-powered candidate screening with expert behavioral analysis. Stop hiring blind. Know who you're getting before you make the offer." />
  <style>
    :root{
      /* Color scheme: Electric Blue, Orange, Gray. Text: Black */
      --blue:#007BFF;          /* electric blue */
      --orange:#FF6A00;        /* vivid orange */
      --gray-900:#1f2937;      /* deep gray */
      --gray-700:#374151;
      --gray-200:#e5e7eb;
      --gray-100:#f3f4f6;
      --white:#ffffff;
      --black:#000000;

      --max:1100px;
      --radius:18px;
      --shadow: 0 10px 30px rgba(31,41,55,.12);
      --shadow-soft: 0 6px 18px rgba(31,41,55,.10);
    }

    *{ box-sizing:border-box; }
    html,body{ margin:0; padding:0; font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji"; color:var(--black); background:linear-gradient(180deg, #ffffff 0%, var(--gray-100) 60%, #ffffff 100%); }
    a{ color:inherit; }
    .wrap{ width: min(var(--max), 92vw); margin: 0 auto; }

    /* Top bar */
    .topbar{
      position:sticky; top:0; z-index:50;
      background:rgba(255,255,255,.92);
      backdrop-filter:saturate(180%) blur(10px);
      border-bottom:1px solid var(--gray-200);
    }
    .topbar .inner{
      display:flex; align-items:center; justify-content:space-between;
      padding:14px 0;
      gap:12px;
    }
    .brand{
      display:flex; align-items:center; gap:10px; font-weight:800; letter-spacing:.2px;
    }
    .badge{
      display:inline-flex; align-items:center; gap:8px;
      padding:6px 10px; border-radius:999px;
      background:linear-gradient(90deg, rgba(0,123,255,.12), rgba(255,106,0,.12));
      border:1px solid rgba(0,0,0,.08);
      font-size:12px;
    }
    .nav{
      display:flex; gap:14px; flex-wrap:wrap;
      font-size:13px;
    }
    .nav a{
      text-decoration:none;
      padding:8px 10px;
      border-radius:999px;
      border:1px solid transparent;
    }
    .nav a:hover{ border-color:rgba(0,0,0,.10); background:rgba(0,0,0,.03); }

    /* Buttons */
    .btn{
      display:inline-flex; align-items:center; justify-content:center;
      padding:12px 16px;
      border-radius:999px;
      border:1px solid rgba(0,0,0,.10);
      background:#fff;
      text-decoration:none;
      font-weight:700;
      box-shadow:var(--shadow-soft);
      transition:transform .08s ease, box-shadow .15s ease, background .15s ease;
      cursor:pointer;
    }
    .btn:hover{ transform: translateY(-1px); box-shadow: var(--shadow); }
    .btn:active{ transform: translateY(0px); box-shadow: var(--shadow-soft); }

    .btn-primary{
      background:linear-gradient(90deg, var(--blue), #2a9bff);
      color:#000; /* per request: black letters */
      border-color: rgba(0,0,0,.12);
    }
    .btn-accent{
      background:linear-gradient(90deg, var(--orange), #ff8a3d);
      color:#000; /* per request */
      border-color: rgba(0,0,0,.12);
    }
    .btn-ghost{
      background:transparent;
      box-shadow:none;
      border-color: rgba(0,0,0,.12);
    }

    /* Hero */
    .hero{
      padding:54px 0 28px;
      position:relative;
      overflow:hidden;
    }
    .hero::before{
      content:"";
      position:absolute; inset:-120px -120px auto -120px;
      height:360px;
      background:
        radial-gradient(220px 220px at 12% 20%, rgba(0,123,255,.22), transparent 60%),
        radial-gradient(260px 260px at 72% 20%, rgba(255,106,0,.20), transparent 62%),
        radial-gradient(380px 380px at 40% 60%, rgba(31,41,55,.10), transparent 65%);
      pointer-events:none;
    }
    .hero-grid{
      position:relative;
      display:grid;
      grid-template-columns: 1.15fr .85fr;
      gap:22px;
      align-items:stretch;
    }
    @media (max-width: 900px){
      .hero-grid{ grid-template-columns: 1fr; }
    }
    h1{
      margin:0 0 10px;
      font-size: clamp(32px, 4vw, 52px);
      line-height:1.05;
      letter-spacing:-.8px;
    }
    .subhead{
      margin:0 0 16px;
      font-size: clamp(16px, 1.6vw, 19px);
      line-height:1.45;
      color: rgba(0,0,0,.80);
      max-width: 58ch;
    }
    .hero-card{
      background:rgba(255,255,255,.92);
      border:1px solid rgba(0,0,0,.10);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding:20px;
    }
    .hero-card h3{
      margin:0 0 10px;
      font-size:16px;
      letter-spacing:.2px;
    }
    .kpis{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:10px;
      margin-top:12px;
    }
    .kpi{
      border-radius:16px;
      padding:12px 12px;
      border:1px solid rgba(0,0,0,.08);
      background: linear-gradient(180deg, rgba(0,0,0,.02), rgba(0,0,0,.00));
    }
    .kpi .num{ font-weight:900; font-size:18px; }
    .kpi .lbl{ font-size:12px; color: rgba(0,0,0,.72); margin-top:2px; }
    .cta-row{
      display:flex; gap:10px; flex-wrap:wrap;
      margin-top:18px;
    }
    .note{
      margin-top:10px;
      font-size:12px;
      color: rgba(0,0,0,.68);
    }

    /* Sections */
    section{ padding:34px 0; }
    .section-title{
      font-size:26px;
      margin:0 0 12px;
      letter-spacing:-.4px;
    }
    .section-lede{
      margin:0 0 18px;
      color: rgba(0,0,0,.78);
      line-height:1.55;
      max-width: 80ch;
    }
    .grid-2{
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:16px;
      align-items:stretch;
    }
    @media (max-width: 900px){
      .grid-2{ grid-template-columns: 1fr; }
    }

    .card{
      background:#fff;
      border:1px solid rgba(0,0,0,.10);
      border-radius: var(--radius);
      box-shadow: var(--shadow-soft);
      padding:18px;
    }
    .card h4{
      margin:0 0 8px;
      font-size:16px;
      letter-spacing:.2px;
    }
    .list{
      margin:10px 0 0;
      padding:0 0 0 18px;
      color: rgba(0,0,0,.80);
      line-height:1.55;
    }

    .steps{
      display:grid;
      grid-template-columns: repeat(5, 1fr);
      gap:10px;
    }
    @media (max-width: 900px){
      .steps{ grid-template-columns: 1fr; }
    }
    .step{
      border-radius: 18px;
      border:1px solid rgba(0,0,0,.10);
      background: linear-gradient(180deg, rgba(0,123,255,.08), rgba(255,106,0,.06));
      padding:14px;
      min-height: 118px;
    }
    .step .n{
      display:inline-flex; align-items:center; justify-content:center;
      width:30px; height:30px; border-radius:999px;
      background:#fff;
      border:1px solid rgba(0,0,0,.12);
      font-weight:900;
      margin-bottom:10px;
    }
    .step p{ margin:0; color: rgba(0,0,0,.82); line-height:1.45; font-size:14px; }

    /* Pricing table */
    .pricing{
      background: linear-gradient(180deg, rgba(31,41,55,.05), rgba(31,41,55,.02));
      border-top:1px solid rgba(0,0,0,.06);
      border-bottom:1px solid rgba(0,0,0,.06);
    }
    table{
      width:100%;
      border-collapse:separate;
      border-spacing:0;
      overflow:hidden;
      border-radius: var(--radius);
      border:1px solid rgba(0,0,0,.10);
      background:#fff;
      box-shadow: var(--shadow-soft);
    }
    th, td{
      padding:14px 14px;
      text-align:left;
      border-bottom:1px solid rgba(0,0,0,.08);
    }
    th{
      background: linear-gradient(90deg, rgba(0,123,255,.12), rgba(255,106,0,.10));
      font-size:13px;
      letter-spacing:.2px;
    }
    tr:last-child td{ border-bottom:none; }
    .price{ font-weight:900; }
    .muted{ color: rgba(0,0,0,.70); }

    /* Add-ons */
    .pill{
      display:inline-flex;
      padding:6px 10px;
      border-radius:999px;
      border:1px solid rgba(0,0,0,.10);
      background:#fff;
      font-size:12px;
      font-weight:700;
      margin-bottom:10px;
    }

    /* CTA footer */
    .cta{
      padding:38px 0 50px;
    }
    .cta-box{
      border-radius: calc(var(--radius) + 6px);
      border:1px solid rgba(0,0,0,.10);
      background:
        radial-gradient(600px 200px at 18% 0%, rgba(0,123,255,.22), transparent 60%),
        radial-gradient(600px 200px at 82% 0%, rgba(255,106,0,.20), transparent 60%),
        #fff;
      box-shadow: var(--shadow);
      padding:22px;
      display:grid;
      grid-template-columns: 1.2fr .8fr;
      gap:14px;
      align-items:center;
    }
    @media (max-width: 900px){
      .cta-box{ grid-template-columns: 1fr; }
    }
    .cta-box h2{
      margin:0 0 6px;
      font-size:24px;
      letter-spacing:-.3px;
    }
    .cta-box p{ margin:0; color: rgba(0,0,0,.82); line-height:1.5; }
    .contact{
      border-radius: var(--radius);
      background: rgba(255,255,255,.85);
      border:1px solid rgba(0,0,0,.10);
      padding:14px;
    }
    .contact .row{ display:flex; gap:8px; flex-wrap:wrap; margin-top:8px; }
    .contact a{ text-decoration:none; }
    .contact .small{ font-size:12px; color: rgba(0,0,0,.75); margin-top:8px; }

    /* Footer */
    footer{
      padding:20px 0 30px;
      color: rgba(0,0,0,.65);
      font-size:12px;
    }
    .hr{ height:1px; background:rgba(0,0,0,.08); margin:18px 0; }
  </style>
</head>

<body>
  <!-- Topbar -->
  <div class="topbar">
    <div class="wrap inner">
      <div class="brand">
        <span class="badge">FERIS™</span>
        <span>Front-End Recruiting Intelligence System</span>
      </div>
      <nav class="nav" aria-label="Page navigation">
        <a href="#how">How it works</a>
        <a href="#pricing">Pricing</a>
        <a href="#addons">Premium add-ons</a>
        <a href="#free">Free profile</a>
        <a href="#team">Team intelligence</a>
      </nav>
      <a class="btn btn-accent" href="#contact">Book a call</a>
    </div>
  </div>

  <!-- Hero -->
  <header class="hero">
    <div class="wrap hero-grid">
      <div class="hero-card">
        <h1>Stop hiring blind.<br/>Know who you’re getting <span style="background:linear-gradient(90deg, rgba(0,123,255,.28), rgba(255,106,0,.24)); padding:0 .25em; border-radius:.35em;">before</span> the offer.</h1>
        <p class="subhead">
          FERIS™ combines AI-guided candidate interviews with expert behavioral analysis so you
          stop wasting time on “good-on-paper” candidates and start interviewing only viable finalists.
        </p>

        <div class="cta-row">
          <a class="btn btn-primary" href="#pricing">See pricing</a>
          <a class="btn btn-ghost" href="#free">Try the free profile</a>
        </div>
        <div class="note">Fast, actionable results. No retainers. No ongoing obligations. Black-letter clarity. ✅</div>

        <div class="kpis" aria-label="Key benefits">
          <div class="kpi">
            <div class="num">48–72 hrs</div>
            <div class="lbl">Typical base turnaround</div>
          </div>
          <div class="kpi">
            <div class="num">15–30 min</div>
            <div class="lbl">AI interview per candidate</div>
          </div>
          <div class="kpi">
            <div class="num">Ranked</div>
            <div class="lbl">Shortlist w/ risk flags</div>
          </div>
        </div>
      </div>

      <aside class="hero-card">
        <h3>The problem</h3>
        <ul class="list">
          <li>Resume floods and low-signal screening</li>
          <li>Phone screens that go nowhere</li>
          <li>Interviews with “paper-strong” misfits</li>
          <li>Expensive bad hires discovered too late</li>
        </ul>
        <div class="hr"></div>
        <h3>The fix</h3>
        <p class="muted" style="margin:0; line-height:1.55;">
          AI handles the volume. I handle judgment. You get intelligence on risk and fit
          before candidates ever hit your calendar.
        </p>
        <div class="cta-row" style="margin-top:14px;">
          <a class="btn btn-accent" href="#contact">Talk about your next hire</a>
        </div>
      </aside>
    </div>
  </header>

  <!-- Problem / Solution -->
  <section>
    <div class="wrap">
      <h2 class="section-title">Hiring shouldn’t feel like roulette.</h2>
      <p class="section-lede">
        Most hiring processes are expensive guessing games. By the time you realize the hire was wrong,
        you’ve already paid in salary, disruption, lost time, and opportunity cost. FERIS™ puts intelligence
        upfront, where decisions are still cheap to change.
      </p>

      <div class="grid-2">
        <div class="card">
          <h4>What FERIS™ delivers</h4>
          <ul class="list">
            <li>Role-specific interview design based on your criteria</li>
            <li>AI-conducted interviews for every candidate</li>
            <li>Expert review of responses for behavioral signals and risk flags</li>
            <li>Ranked shortlist with clear “worth your time” notes</li>
          </ul>
        </div>
        <div class="card">
          <h4>What you stop doing</h4>
          <ul class="list">
            <li>Reading piles of resumes and guessing</li>
            <li>Phone screening your entire pipeline</li>
            <li>Scheduling interviews with candidates who won’t fit</li>
            <li>Hiring on hope and discovering problems later</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- How it works -->
  <section id="how">
    <div class="wrap">
      <h2 class="section-title">How it works</h2>
      <p class="section-lede">Simple flow. Clear output. You get decision-grade intelligence, fast.</p>

      <div class="steps">
        <div class="step">
          <div class="n">1</div>
          <p><strong>You share</strong> the job description and hiring criteria.</p>
        </div>
        <div class="step">
          <div class="n">2</div>
          <p><strong>I design</strong> a custom interview for your role and success markers.</p>
        </div>
        <div class="step">
          <div class="n">3</div>
          <p><strong>Candidates complete</strong> the AI interview (15–30 minutes each).</p>
        </div>
        <div class="step">
          <div class="n">4</div>
          <p><strong>I review</strong> every response for behavioral signals, risk, and fit.</p>
        </div>
        <div class="step">
          <div class="n">5</div>
          <p><strong>You receive</strong> a ranked shortlist and interview guidance.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Pricing -->
  <section id="pricing" class="pricing">
    <div class="wrap">
      <h2 class="section-title">Base service pricing</h2>
      <p class="section-lede">
        Custom interview design + AI-led interviews + <strong>personal analysis of every response</strong>.
        Delivered in 48–72 hours.
      </p>

      <table aria-label="Base service pricing tiers">
        <thead>
          <tr>
            <th>Candidate Volume</th>
            <th>Price</th>
            <th>Notes</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>0–25</td>
            <td class="price">$499</td>
            <td class="muted">Best for a single opening with moderate interest</td>
          </tr>
          <tr>
            <td>26–50</td>
            <td class="price">$999</td>
            <td class="muted">Higher volume, faster filtering</td>
          </tr>
          <tr>
            <td>51–100</td>
            <td class="price">$1,999</td>
            <td class="muted">Multiple openings or high applicant flow</td>
          </tr>
          <tr>
            <td>101–200</td>
            <td class="price">$3,499</td>
            <td class="muted">Large pipelines, active recruiting</td>
          </tr>
          <tr>
            <td>200+</td>
            <td class="price">Custom</td>
            <td class="muted">Enterprise / ongoing sourcing</td>
          </tr>
        </tbody>
      </table>

      <div class="grid-2" style="margin-top:16px;">
        <div class="card">
          <h4>Included at every tier</h4>
          <ul class="list">
            <li>Role-specific interview structure</li>
            <li>AI interviews for all candidates</li>
            <li><strong>Expert review</strong> of every response</li>
            <li>Behavioral risk and fit screening</li>
            <li>Ranked shortlist with intelligence notes</li>
          </ul>
        </div>
        <div class="card">
          <h4>Typical outcomes</h4>
          <ul class="list">
            <li>Fewer wasted interviews</li>
            <li>Faster shortlisting</li>
            <li>Clearer “why this person” reasoning</li>
            <li>Reduced risk of bad-fit hires</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- Premium Add-ons -->
  <section id="addons">
    <div class="wrap">
      <h2 class="section-title">Premium add-ons: deep intelligence on finalists</h2>
      <p class="section-lede">
        When you’re down to finalists, I can run deeper screening to help you make the final call with confidence.
      </p>

      <div class="grid-2">
        <div class="card">
          <div class="pill">Top 3 Deep Screen</div>
          <h4>$1,500</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Mid-level profile with a focused live interview (15–20 minutes per candidate).
          </p>
          <ul class="list">
            <li>I conduct live interviews with your top 3 candidates</li>
            <li>Motivations and drivers</li>
            <li>Strengths and fit indicators</li>
            <li>Team vs solo orientation</li>
            <li>Internal vs external locus of control</li>
            <li>Character and needs assessment</li>
          </ul>
        </div>

        <div class="card">
          <div class="pill">Top 3 + Culture Fit Analysis</div>
          <h4>$3,000</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Extended analysis with organizational fit assessment (45–60 minutes per candidate).
          </p>
          <ul class="list">
            <li>Everything in Deep Screen</li>
            <li>Culture and values alignment</li>
            <li>Leadership style compatibility</li>
            <li>Predictable friction points in your environment</li>
            <li>Risk assessment for culture clash</li>
            <li>Onboarding guidance</li>
          </ul>
        </div>
      </div>

      <div class="grid-2" style="margin-top:16px;">
        <div class="card">
          <div class="pill">Top 3 + Full Team Fit Analysis</div>
          <h4>$5,000</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Complete integration intelligence (candidates + existing team).
          </p>
          <ul class="list">
            <li>Everything in Culture Fit Analysis</li>
            <li>Profiles of 3–5 existing team members</li>
            <li>Predictable interpersonal friction or synergy points</li>
            <li>Team dynamics map showing integration points</li>
            <li>Management and communication strategy per candidate</li>
          </ul>
        </div>

        <div class="card">
          <div class="pill">Additional Deep Screen</div>
          <h4>$1,000 each</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Need deeper intelligence on candidates beyond the top 3? Add them as needed.
          </p>
          <ul class="list">
            <li>Live interview + written analysis</li>
            <li>Risk and fit indicators</li>
            <li>Actionable guidance for your interview process</li>
            <li>Typical turnaround: 5–7 business days for premium work</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- Free Profile -->
  <section id="free" class="pricing">
    <div class="wrap">
      <h2 class="section-title">Start here: free profile</h2>
      <p class="section-lede">
        Not sure if FERIS™ will work for your hiring process?
        I’ll do a complimentary behavioral profile of someone you already know:
        an existing employee, a recent hire, or even yourself.
      </p>

      <div class="grid-2">
        <div class="card">
          <h4>What you get</h4>
          <ul class="list">
            <li>Brief interview or analysis</li>
            <li>Motivations and working style</li>
            <li>Risk factors and predictable patterns</li>
            <li>Practical management/communication insights</li>
          </ul>
        </div>
        <div class="card">
          <h4>Why it’s offered</h4>
          <ul class="list">
            <li>So you can see how accurately I read someone you already know</li>
            <li>So you can trust the intelligence on candidates you don’t</li>
            <li>No obligation. No pressure. Just clarity.</li>
          </ul>
          <div class="cta-row">
            <a class="btn btn-accent" href="#contact">Request the free profile</a>
            <a class="btn btn-ghost" href="#pricing">Review pricing</a>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Internal Team Intelligence -->
  <section id="team">
    <div class="wrap">
      <h2 class="section-title">Also available: internal team intelligence</h2>
      <p class="section-lede">
        Sometimes the problem isn’t hiring. It’s what’s already happening inside the team.
        If you want clarity on risk, fit, friction, and repeating patterns, these services apply the same behavioral intelligence internally.
      </p>

      <div class="grid-2">
        <div class="card">
          <div class="pill">Individual Risk & Fit Analysis</div>
          <h4>$1,250</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Understand what’s really happening with a specific employee: risk, fit, or management issue.
          </p>
          <ul class="list">
            <li>Behavioral profile and operating style</li>
            <li>Predictable failure points and friction sources</li>
            <li>Clear guidance: reposition, support, or exit</li>
          </ul>
        </div>

        <div class="card">
          <div class="pill">Team Dynamics Analysis</div>
          <h4>$3,500</h4>
          <p class="muted" style="margin:0 0 10px; line-height:1.55;">
            Identify friction sources, power patterns, and why the same problems keep repeating.
          </p>
          <ul class="list">
            <li>Mini-profiles of key contributors</li>
            <li>Team dynamics map (influence + conflict vectors)</li>
            <li>3 corrective levers leadership can pull immediately</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- Final CTA -->
  <section class="cta" id="contact">
    <div class="wrap">
      <div class="cta-box">
        <div>
          <h2>Ready to hire smarter?</h2>
          <p>
            If one bad hire costs more than $499, FERIS™ pays for itself the first time you use it.
            Let’s talk about your next role and whether this fits your hiring process.
          </p>
        </div>
        <div class="contact">
          <strong>Joseph McElveen</strong><br/>
          <span class="muted">Recruiting Intelligence Specialist</span>
          <div class="row">
            <a class="btn btn-primary" href="tel:6789948509">Call: 678-994-8509</a>
            <a class="btn btn-accent" href="mailto:josephmcelveen@pm.me">Email: josephmcelveen@pm.me</a>
          </div>
          <div class="small">Tip: Replace contact details or add a scheduling link when you’re ready.</div>
        </div>
      </div>

      <footer>
        <div class="hr"></div>
        <div class="wrap" style="width:100%; margin:0;">
          <div style="display:flex; justify-content:space-between; gap:12px; flex-wrap:wrap;">
            <span>© <span id="y"></span> FERIS™</span>
            <span class="muted">Electric Blue • Orange • Gray | Black text</span>
          </div>
        </div>
      </footer>
    </div>
  </section>

  <script>
    document.getElementById("y").textContent = new Date().getFullYear();
  </script>
</body>
</html>
```0
