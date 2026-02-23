
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
