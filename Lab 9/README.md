
<div class="container">

  <!-- Badges -->
  <div class="badge-row">
    <span class="badge badge-purple">Lab 9</span>
    <span class="badge badge-red">Causal Inference</span>
    <span class="badge badge-grey">Lalonde 1986 — Observational Subset</span>
  </div>

  <!-- Hero -->
  <div class="hero">
    <h1>Recovering Experimental Truths via Propensity Score Matching</h1>
    <div class="subtitle">Causal Identification · Selection Bias Correction · ATT Estimation</div>
    <p>
      Observational data is <strong>broken by design</strong>. Without randomization, selection bias doesn't
      merely add noise — it can invert the sign of your conclusions entirely. This project deploys
      <strong>Propensity Score Matching</strong> to surgically remove that bias and recover the true
      causal effect from data that, in its raw form, produces a dangerously wrong answer.
    </p>
  </div>

  <!-- Bias Compare -->
  <div class="section-label">The Problem — and the Fix</div>
  <div class="bias-compare">
    <div class="bias-box wrong">
      <div class="label">Naïve Estimate (Unmatched)</div>
      <div class="value">–$15,204</div>
      <div class="sub">Directionally wrong · Selection bias dominates</div>
    </div>
    <div class="arrow-col">
      <div class="psm-label">PSM</div>
      <div class="arrow">→</div>
      <div class="delta">Δ ~$17,004<br>bias corrected</div>
    </div>
    <div class="bias-box right">
      <div class="label">PSM-Matched ATT</div>
      <div class="value">+$1,800</div>
      <div class="sub">Consistent with experimental benchmark</div>
    </div>
  </div>

  <!-- Objective -->
  <div class="card">
    <div class="card-header">
      <span class="icon">🎯</span>
      <h2>Objective</h2>
      <span class="tag">Fixing Observational Failure</span>
    </div>
    <div class="card-body">
      <div style="background:#1a1230;border:1px solid #6e40c9;border-radius:6px;padding:16px 20px;color:#c9d1d9;font-size:14.5px;">
        Demonstrate that naïve treatment effect estimation on observational data is not merely imprecise —
        it is <strong style="color:#f85149;">structurally unreliable</strong>. Apply Propensity Score Matching
        to balance the covariate distributions of treated and control groups, reconstruct a credible
        counterfactual, and recover a causal estimate that matches the experimental ground truth.
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

      <div class="step">
        <div class="step-num">1</div>
        <div class="step-content">
          <h3>Modeling Selection Bias — The Propensity Score</h3>
          <ul>
            <li>Built a <strong style="color:#c9d1d9;">logistic regression model</strong> (Scikit-Learn) to estimate P(D=1 | X) for each unit</li>
            <li>Covariates: age, education, race, prior earnings, marital status</li>
            <li>Collapses high-dimensional covariate space into a single comparable scalar</li>
          </ul>
        </div>
      </div>
      <div class="connector"></div>

      <div class="step">
        <div class="step-num">2</div>
        <div class="step-content">
          <h3>Constructing the Counterfactual — Nearest-Neighbor Matching</h3>
          <ul>
            <li>Each treated unit matched to its <strong style="color:#c9d1d9;">nearest control neighbor</strong> by propensity score distance</li>
            <li>Matching with replacement — no treated unit left without a credible counterfactual</li>
            <li>Post-matching covariate distributions inspected to validate balance</li>
          </ul>
        </div>
      </div>
      <div class="connector"></div>

      <div class="step">
        <div class="step-num">3</div>
        <div class="step-content">
          <h3>Estimating the ATT — Average Treatment Effect on the Treated</h3>
          <ul>
            <li>ATT computed as mean outcome difference across all matched pairs</li>
            <li>Compared against naïve OLS estimate to quantify selection bias magnitude</li>
            <li>Validated against Lalonde experimental benchmark</li>
          </ul>
        </div>
      </div>

    </div>
  </div>

  <!-- Key Findings Table -->
  <div class="card">
    <div class="card-header">
      <span class="icon">📊</span>
      <h2>Key Findings</h2>
    </div>
    <div class="card-body">
      <table class="results-table">
        <thead>
          <tr>
            <th>Estimator</th>
            <th>Treatment Effect</th>
            <th>Interpretation</th>
          </tr>
        </thead>
        <tbody>
          <tr class="bad">
            <td>Naïve OLS (Unmatched)</td>
            <td>~ –$15,204</td>
            <td>Severely biased; selection bias inverts the sign entirely</td>
          </tr>
          <tr class="good">
            <td>PSM-Matched ATT</td>
            <td>~ +$1,800</td>
            <td>Consistent with experimental RCT benchmark</td>
          </tr>
          <tr class="delta">
            <td>Total Bias Corrected</td>
            <td>~ +$17,004</td>
            <td>The quantified cost of skipping causal identification</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- Technical -->
  <div class="card">
    <div class="card-header">
      <span class="icon">🛠️</span>
      <h2>Technical Stack</h2>
    </div>
    <div class="card-body">
      <p style="color:#8b949e;font-size:14.5px;margin-bottom:12px;">
        Nearest-neighbor matching on the propensity score, with replacement. Post-matching covariate
        balance validated visually and statistically. PSM estimate explicitly benchmarked against
        the Lalonde experimental RCT to confirm recovery of the true treatment effect.
      </p>
      <div class="tech-row">
        <span class="pill pill-purple">scikit-learn — LogisticRegression</span>
        <span class="pill pill-blue">pandas — covariate matrix</span>
        <span class="pill pill-green">numpy — ATT computation</span>
        <span class="pill pill-purple">Nearest-Neighbor Matching</span>
        <span class="pill pill-blue">Covariate Balance Validation</span>
        <span class="pill pill-green">RCT Benchmark Comparison</span>
      </div>
    </div>
  </div>

  <!-- Business Insight -->
  <div class="card">
    <div class="card-header">
      <span class="icon">💡</span>
      <h2>Business Insight: Observational Naïveté Is a Career Risk</h2>
    </div>
    <div class="card-body">
      <div class="insight-box">
        Every A/B test that fails to run, every product decision drawn from dashboard metrics, every
        "data-driven" conclusion from non-experimental data carries an invisible tax:
        <span class="hl-orange">selection bias</span>. Users who opted into a feature are not the
        same as those who did not. Treating observational data as experimental is not a minor
        methodological oversight — as this lab demonstrates, it can
        <span class="hl-orange">invert the sign of your conclusions entirely</span>.<br><br>
        <span class="hl-purple">Propensity Score Matching</span> is the backbone of policy evaluation
        at institutions from the World Bank to Uber's experimentation platform. The ability to identify
        <em>when</em> observational data is untrustworthy — and apply the correct correction — is what
        separates a data scientist from a data reporter.
      </div>
    </div>
  </div>

  <div class="footer">Lab 9 · Lalonde (1986) NSW Job Training Program — Observational Subset · Python: scikit-learn, pandas, numpy</div>

</div>
</body>
</html>
