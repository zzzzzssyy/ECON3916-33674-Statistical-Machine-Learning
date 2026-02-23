<!DOCTYPE html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lab 8 — The Epistemology of Falsification</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    background: #0d1117;
    color: #e6edf3;
    line-height: 1.7;
    padding: 40px 20px;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
  }

  /* ── TOP BADGE ── */
  .badge-row {
    display: flex;
    gap: 10px;
    margin-bottom: 28px;
    flex-wrap: wrap;
  }
  .badge {
    font-size: 12px;
    font-weight: 600;
    padding: 4px 12px;
    border-radius: 20px;
    letter-spacing: .5px;
    text-transform: uppercase;
  }
  .badge-blue  { background: #1f3a5f; color: #58a6ff; border: 1px solid #2d6aa0; }
  .badge-green { background: #1a3a2a; color: #3fb950; border: 1px solid #238636; }
  .badge-grey  { background: #21262d; color: #8b949e; border: 1px solid #30363d; }

  /* ── HERO ── */
  .hero {
    border: 1px solid #30363d;
    border-top: 3px solid #58a6ff;
    border-radius: 10px;
    padding: 36px 40px;
    background: #161b22;
    margin-bottom: 32px;
  }
  .hero h1 {
    font-size: 26px;
    font-weight: 700;
    color: #ffffff;
    margin-bottom: 8px;
  }
  .hero .subtitle {
    color: #58a6ff;
    font-size: 14px;
    font-weight: 500;
    letter-spacing: .4px;
    margin-bottom: 18px;
  }
  .hero p {
    color: #8b949e;
    font-size: 15px;
  }
  .hero strong { color: #c9d1d9; }

  /* ── SECTION CARD ── */
  .card {
    border: 1px solid #30363d;
    border-radius: 10px;
    background: #161b22;
    margin-bottom: 24px;
    overflow: hidden;
  }
  .card-header {
    padding: 16px 24px;
    border-bottom: 1px solid #30363d;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .card-header .icon {
    font-size: 18px;
  }
  .card-header h2 {
    font-size: 16px;
    font-weight: 600;
    color: #e6edf3;
  }
  .card-header .tag {
    margin-left: auto;
    font-size: 11px;
    color: #8b949e;
    background: #21262d;
    padding: 2px 8px;
    border-radius: 4px;
    border: 1px solid #30363d;
  }
  .card-body {
    padding: 24px;
  }

  /* ── OBJECTIVE BOX ── */
  .objective-box {
    background: #0d2137;
    border: 1px solid #1f3a5f;
    border-left: 3px solid #58a6ff;
    border-radius: 6px;
    padding: 16px 20px;
    margin-bottom: 20px;
    color: #c9d1d9;
    font-size: 14.5px;
  }

  /* ── METHODS GRID ── */
  .method-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 20px;
  }
  @media (max-width: 600px) { .method-grid { grid-template-columns: 1fr; } }

  .method-box {
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 18px;
    background: #0d1117;
  }
  .method-box h3 {
    font-size: 13px;
    font-weight: 700;
    color: #58a6ff;
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: .5px;
  }
  .method-box ul {
    list-style: none;
    padding: 0;
  }
  .method-box ul li {
    font-size: 13.5px;
    color: #8b949e;
    padding: 4px 0;
    padding-left: 14px;
    position: relative;
  }
  .method-box ul li::before {
    content: "→";
    position: absolute;
    left: 0;
    color: #3fb950;
  }

  /* ── FINDING ── */
  .finding {
    background: #12261a;
    border: 1px solid #238636;
    border-radius: 8px;
    padding: 20px 24px;
    display: flex;
    align-items: flex-start;
    gap: 16px;
    margin-bottom: 20px;
  }
  .finding .amount {
    font-size: 32px;
    font-weight: 800;
    color: #3fb950;
    white-space: nowrap;
    line-height: 1;
    padding-top: 2px;
  }
  .finding .desc {
    font-size: 14.5px;
    color: #c9d1d9;
  }
  .finding .desc strong { color: #3fb950; }

  /* ── TECH PILLS ── */
  .tech-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 14px;
  }
  .pill {
    font-size: 12px;
    padding: 4px 10px;
    border-radius: 20px;
    font-weight: 500;
  }
  .pill-blue   { background: #1f3a5f; color: #79c0ff; border: 1px solid #2d6aa0; }
  .pill-green  { background: #1a3a2a; color: #56d364; border: 1px solid #238636; }
  .pill-orange { background: #3d2000; color: #f0883e; border: 1px solid #9a4b00; }

  /* ── INSIGHT ── */
  .insight-intro {
    font-size: 14.5px;
    color: #8b949e;
    margin-bottom: 18px;
  }
  .risk-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-bottom: 20px;
  }
  @media (max-width: 640px) { .risk-grid { grid-template-columns: 1fr; } }
  .risk-box {
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 14px;
    background: #0d1117;
    text-align: center;
  }
  .risk-box .risk-icon { font-size: 22px; margin-bottom: 6px; }
  .risk-box .risk-name {
    font-size: 12px;
    font-weight: 700;
    color: #f85149;
    text-transform: uppercase;
    letter-spacing: .4px;
    margin-bottom: 6px;
  }
  .risk-box p {
    font-size: 12px;
    color: #8b949e;
  }
  .insight-footer {
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 16px 20px;
    font-size: 14px;
    color: #8b949e;
    font-style: italic;
  }
  .insight-footer em { color: #58a6ff; font-style: normal; font-weight: 600; }

  /* ── DIVIDER ── */
  .section-label {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: #30363d;
    margin: 36px 0 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-label::before, .section-label::after {
    content: "";
    flex: 1;
    height: 1px;
    background: #30363d;
  }

  /* ── PROMPT 2 ── */
  .concept-box {
    background: #0d1117;
    border: 1px solid #30363d;
    border-left: 3px solid #f0883e;
    border-radius: 6px;
    padding: 20px 24px;
    font-size: 15px;
    color: #c9d1d9;
    line-height: 1.8;
  }
  .concept-box .highlight { color: #f0883e; font-weight: 700; }
  .concept-box .highlight2 { color: #58a6ff; font-weight: 600; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    color: #30363d;
    font-size: 12px;
    margin-top: 40px;
  }
</style>
</head>
<body>
<div class="container">

  <!-- Badges -->
  <div class="badge-row">
    <span class="badge badge-blue">Lab 8</span>
    <span class="badge badge-green">Hypothesis Testing</span>
    <span class="badge badge-grey">Lalonde 1986 Dataset</span>
  </div>

  <!-- Hero -->
  <div class="hero">
    <h1>The Epistemology of Falsification</h1>
    <div class="subtitle">Hypothesis Testing on the Lalonde Dataset</div>
    <p>
      The guiding question is not <strong>"What is the treatment effect?"</strong> — it is
      <strong>"Can the Null Hypothesis of zero effect be credibly rejected, and under what
      conditions does that rejection hold?"</strong> This project operationalizes a shift from
      <em>Estimation</em> to <em>Falsification</em>.
    </p>
  </div>

  <!-- ── README Content ── -->
  <div class="section-label">Prompt 1 — README.md · Lab 8 Folder</div>

  <!-- Objective -->
  <div class="card">
    <div class="card-header">
      <span class="icon">🎯</span>
      <h2>Objective</h2>
      <span class="tag">Project Title: Hypothesis Testing & Causal Evidence Architecture</span>
    </div>
    <div class="card-body">
      <div class="objective-box">
        Using the Lalonde (1986) dataset, I adjudicate between competing narratives of causality
        to determine whether a job training intervention produced a measurable effect on real
        earnings. The analytical philosophy pivots from <strong>Estimation</strong> (reporting a
        number) to <strong>Falsification</strong> (stress-testing a claim against a principled
        null model).
      </div>
    </div>
  </div>

  <!-- Methodology -->
  <div class="card">
    <div class="card-header">
      <span class="icon">⚙️</span>
      <h2>Methodology</h2>
    </div>
    <div class="card-body">
      <div class="method-grid">
        <div class="method-box">
          <h3>Parametric — Welch's T-Test</h3>
          <ul>
            <li>Estimated Average Treatment Effect (ATE) on 1978 real earnings</li>
            <li>Welch's formulation handles unequal variances between groups</li>
            <li>Produced t-statistic and p-value under normal sampling assumption</li>
            <li>Type I error controlled at explicit α threshold</li>
          </ul>
        </div>
        <div class="method-box">
          <h3>Non-Parametric — Permutation Test</h3>
          <ul>
            <li>10,000 resamples to build empirical null distribution</li>
            <li>Robust to right-skewed, zero-inflated earnings data</li>
            <li>Validates parametric result without distributional assumptions</li>
            <li>Convergence of both methods strengthens inference</li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <!-- Key Finding -->
  <div class="card">
    <div class="card-header">
      <span class="icon">📊</span>
      <h2>Key Findings</h2>
    </div>
    <div class="card-body">
      <div class="finding">
        <div class="amount">+$1,795</div>
        <div class="desc">
          Statistically significant lift in real earnings for job training participants.
          <strong>Null Hypothesis rejected</strong> via Proof by Statistical Contradiction —
          results consistent across both parametric and non-parametric frameworks, ruling out
          distributional artifacts as a confounding explanation.
        </div>
      </div>
    </div>
  </div>

  <!-- Technical Approach -->
  <div class="card">
    <div class="card-header">
      <span class="icon">🛠️</span>
      <h2>Technical Approach</h2>
    </div>
    <div class="card-body">
      <p style="color:#8b949e;font-size:14.5px;margin-bottom:12px;">
        Dual-method validation deployed in parallel to cross-validate conclusions and guard against model misspecification.
        Significance threshold explicitly set and justified — acknowledging that α is a <em>decision boundary</em> calibrated to
        the cost of false positives, not a universal scientific default.
      </p>
      <div class="tech-row">
        <span class="pill pill-blue">scipy.stats — T-Test</span>
        <span class="pill pill-green">numpy — Permutation Resampling</span>
        <span class="pill pill-orange">Random Seed Fixed — Reproducible</span>
        <span class="pill pill-blue">Type I Error Control</span>
        <span class="pill pill-green">Welch's Formulation</span>
      </div>
    </div>
  </div>

  <!-- Business Insight -->
  <div class="card">
    <div class="card-header">
      <span class="icon">💡</span>
      <h2>Business Insight: Hypothesis Testing as the Safety Valve</h2>
    </div>
    <div class="card-body">
      <p class="insight-intro">
        In the modern data economy, calculating a statistic is a commodity.
        The scarce skill is <strong style="color:#e6edf3;">Causal Evidence Architecture</strong> —
        designing tests that distinguish genuine signal from noise. Without rigorous hypothesis testing,
        organizations fall prey to:
      </p>
      <div class="risk-grid">
        <div class="risk-box">
          <div class="risk-icon">🎲</div>
          <div class="risk-name">Data Grubbing</div>
          <p>Iterating over metrics until significance appears by chance, inflating false discovery rates.</p>
        </div>
        <div class="risk-box">
          <div class="risk-icon">🔀</div>
          <div class="risk-name">Spurious Correlations</div>
          <p>Optimizing on patterns that don't generalize, leading to flawed product decisions at scale.</p>
        </div>
        <div class="risk-box">
          <div class="risk-icon">🪄</div>
          <div class="risk-name">Survivorship Bias</div>
          <p>Drawing conclusions from visible outcomes while ignoring the data-generating process.</p>
        </div>
      </div>
      <div class="insight-footer">
        Companies like Netflix and Uber don't ask "Is the p-value below 0.05?" — they ask
        <em>"Is the experimental design valid?"</em> and
        <em>"Are we controlling for the right confounders?"</em>
        This project treats hypothesis testing not as a checklist item, but as a framework for
        principled belief revision under uncertainty.
      </div>
    </div>
  </div>

  <!-- ── Prompt 2 ── -->
  <div class="section-label">Prompt 2 — Concept Extension · Portfolio README</div>

  <div class="card">
    <div class="card-header">
      <span class="icon">🧠</span>
      <h2>Return-Aware Experimentation — Concept Extension</h2>
      <span class="tag">3–4 sentences · Portfolio-ready</span>
    </div>
    <div class="card-body">
      <div class="concept-box">
        <span class="highlight">Return-Aware Experimentation</span> is Netflix's framework for
        calibrating decision thresholds to the <em>asymmetric cost of errors</em>, rather than
        applying a uniform p &lt; 0.05 standard borrowed from academic convention. Where academic
        statistics treats α = 0.05 as a near-universal norm, Netflix recognizes that the cost of a
        false positive (shipping a harmful feature to 200M users) is categorically different from
        the cost of a false negative (delaying a beneficial one). This means
        <span class="highlight2">decision thresholds are business parameters</span> — tuned to
        the revenue, risk, and reversibility of each specific decision — not immutable scientific
        laws. I apply this principle by treating my significance thresholds as explicit choices I
        can defend, not defaults I inherit.
      </div>
    </div>
  </div>

  <div class="footer">Lab 8 · Lalonde (1986) NSW Job Training Program · Python: scipy, numpy</div>

</div>
</body>
</html>
