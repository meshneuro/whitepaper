---
layout: default
title: NeuroMesh Whitepaper
---

# NeuroMesh: The Humanoid Intelligence Layer Forming a Decentralised Superbrain

*RWA × AI × Robotics × Compute × Data — Version 2025 — Research concept paper (not an investment solicitation)*

---

## Abstract

NeuroMesh defines a humanoid-first intelligence layer on Solana that any robot can install to become software-defined, safety-bounded, and market-connected. Each robot runs agentic cognition locally (on-robot CPU/NPU/GPU), generating verifiable “thoughts” and “actions” recorded as Composite Thought/Action Vectors (CTV/A) with lineage, evaluator scores, and royalty rules. All inference and learning compute is executed **on the robot**; tokenised compute credits (**cCOMP**) are minted solely from **attested on-robot cycles**. The economy further tokenises **embodied minutes** (**nROBOT**), **energy windows** (**nENERGY**), **durable storage** (**nSTOR**), and—critically—**data as a Real-World Asset** through **per-robot data rights** (**nDATA-R**), whose ownership is anchored by a **Data Ownership Certificate (DOC)** and a **Perception Lineage ID (PLID)**. Correctness is enforced by Proof-of-Inference (PoI) and optional zkML; embodied safety by Control Barrier Certificates (CBC) and Proof-of-Action (PoA). A model-predictive controller (MPC) tunes verification overhead, queueing, and safety risk while dual-descent pricing clears resources. As robots perceive more of the world, data, skills, and incentives reinforce each other so the network behaves like a single **decentralised superbrain**: an organism whose intelligence density compounds with lived experience.

---

## 1. Motivation and Thesis

1. **Embodiment has arrived.** Useful autonomy lives inside tight latency budgets (≈10–800 ms), privacy regimes, human-aware safety envelopes, and energy constraints.
2. **Intelligence must be priced under constraints.** Capability is not just model quality; it is quality **subject to** safety, latency, energy, and rights.
3. **Ownership matters.** “He who owns the data owns the future.” Ownership must be cryptographically provable, economically valued, and enforceable at the edge.
4. **Therefore:** put cognition on the robot; expose rights, safety and verification as first-class; tokenise compute, capability and **data**; and settle on a fast, low-cost chain.

---

## 2. Historical Context (condensed)

- **Time-sharing → Cloud.** Centralised compute with generous latency tolerances.
- **Deep Learning Era.** Disembodied models dominated, largely off-device.
- **Embodiment Era (now).** Sensorimotor context, human interaction, and jurisdictional privacy shift learning on-device; verification and safety become economic primitives.

---

## 3. Core Concepts and Notation

- **Agents & robots.** Each wallet can host an agent; each robot runs NeuroOS-H (humanoid OS) and presents **on-robot** compute, skills, safety, and data vaults.
- **CTV/A.** A verifiable artefact containing inputs, outputs, evaluators’ notes, PoI/PoA receipts, lineage, and royalty curves.
- **Tokens.**
  - **$NEURO$:** base fees, staking, governance.
  - **cCOMP:** attested **on-robot** compute credits; burn-to-use.
  - **nROBOT:** embodied minutes by safety class.
  - **nENERGY:** time-of-use/PPAs anchoring carbon/price.
  - **nSTOR:** durable storage with region/SLA.
  - **nDATA:** licensed catalogue datasets (third-party).
  - **nDATA-R:** **per-robot data rights** (the RWA of experience).
  - **iCTVs:** rights to CTV/A (reuse + ALR-scoped learning royalties).
- **Intelligence density.**
  $$
  I = \log N \cdot \bar{\beta} \cdot C
  $$
  where $N$ is active robots/agents, $\bar{\beta}$ useful message rate, and $C$ coherence (fraction of high-quality CTV/A).
- **Verification overhead.**
  $$
  \psi \in [0,1), \qquad \chi = \frac{\psi}{1-\psi}
  $$
- **PoI tail bound.**
  $$
  P_{\mathrm{FA}} \approx \exp\!\bigl(-2q(1/2-\theta)^2\bigr)
  \quad \Rightarrow \quad
  q \ge \frac{\ln(1/\varepsilon)}{2(1/2-\theta)^2}
  $$
- **Safety.** $ P\_{\mathrm{unsafe}} \le \varepsilon\_s $; CBC constraints embedded in control.

---

## 4. Architecture (Humanoid-First)

### 4.1 NeuroOS-H

- **Control plane:** torque/impedance controllers at 500–2,000 Hz; reflex arcs ≤20 ms; servo jitter ≤2 ms.
- **Perception:** RGB-D, event cameras, microphones, tactile skins, force–torque, IMU, encoders.
- **Policy server:** option library $ \{\pi_{\mathrm{nav}}, \pi_{\mathrm{grasp}}, \pi_{\mathrm{tool}}, \pi_{\mathrm{social}}\} $ with confidence scores, termination sets, and ALR hooks.
- **Safety supervisor:** CBC, geofences, human-aware envelopes; teleoperation fall-back when confidence $< \tau$.
- **Secure logger:** TPM/TEE-attested, hash-chained sensorimotor logs and actuation streams.
- **Mesh daemon:** discovery, pricing, escrow, receipts; PoI/PoA clients.

### 4.2 Sense → Think → Act (market primitive)

A task $ \tau=(g,d,\kappa,\Pi) $ produces:

- **Sense** $ z=\phi_{\mathrm{sense}}(d) $ (multimodal μTokens),
- **Think** $ a^\*=\arg\max_a \mathbb{E}[R \mid z,g,\kappa,\Pi] $ under CBC,
- **Act** $ u(t) $ with PoA receipts,
- **Learn** $ \Delta K $ (self-supervised objectives, ALR budgets).
  Artefacts settle as **CTV/A**; **all compute** runs **on the robot**.

---

## 5. Tokenisation Stack (with Data as RWA)

### 5.1 Instruments

- **$NEURO$:** Fees, staking, governance.
- **cCOMP (on-robot):**
  $$
  \Delta \mathrm{cCOMP} = \kappa_{\mathrm{attest}} \cdot r_{\mathrm{clk}} \cdot \Delta t
  $$
  where $\kappa_{\mathrm{attest}} \in \{0,1\}$ proves OS/accelerator state and SLO adherence; burn-to-use.
- **nROBOT:** Minutes by safety class and attestation.
- **nENERGY:** Energy windows/PPAs; metering oracle; region.
- **nSTOR:** Storage capacity with durability and locality.
- **nDATA (catalogue):** Licenced datasets with ALR scope.
- **nDATA-R (per-robot data rights):** **Tokenised ownership of a robot’s own captured experience**, bound to:
  - **DOC (Data Ownership Certificate).** Operator DID, robot DID, OS/accelerator attestation hash, time window, site, modality map, capture policy, PLID, signature.
  - **PLID (Perception Lineage ID).** Merkle root over hashed, windowed perception logs, signed inside TEE.

### 5.2 Execution bundle and placement

Execution bundle: {cCOMP\_on-robot, iCTVs, nROBOT slice, optional nDATA/nDATA-R, optional nENERGY}.  
Placement is **on-robot**; $L_{\mathrm{net}} \approx 0$ for inference; safety policies remain local.

### 5.3 Solvency and issuance

For each tranche $r$:

$$
\text{NAV}_r = PV(\text{cashflows}_r) - \text{liabilities}_r - \text{reserves}_r,
$$
$$
\sum_r \text{issued}_r \cdot \text{unit\_value}_r \le \sum_r \text{NAV}_r \bigl(1-h_r\bigr).
$$
**nDATA-R** lots may be aggregated into tranches with similar modality mix, safety class, site category, and ALR defaults; NAV reflects **expected licensing cash-flows** (Section 10).

---

## 6. Data Ownership & Rights (nDATA-R)

### 6.1 Minting flow

1) **Capture:** robot records sensorimotor streams into an encrypted local vault.  
2) **Attest:** TEE signs OS/accelerator measurement; mesh daemon rotates windowed hashes → **PLID**.  
3) **Certify:** generate **DOC** (ownership/conditions); hash the policy manifest (ALR defaults).  
4) **Mint:** issue **nDATA-R lot** $(\mathrm{DOC}, \mathrm{PLID}, \mathrm{modality\_mix}, \mathrm{ALR}_0, \mathrm{royalty\_curve}, \mathrm{expiry})$.  
5) **List:** optional listing on the data market with reserve/ask and usage restrictions.

**Principle:** **raw data never leaves** the vault; licences concern μTokens/statistics and **explicit learning rights**.

### 6.2 ALR (Agentic Learning Rights)

ALR expresses purpose (e.g., “grasp stability”), forbids classes (e.g., face identification), and allocates privacy budgets $(\varepsilon,\delta)$. Composition bound:

$$
\varepsilon_{\mathrm{total}} \le \sqrt{2T \ln(1/\delta)}\,\bar{\varepsilon}
 + T\,\bar{\varepsilon}\,\bigl(e^{\bar{\varepsilon}}-1\bigr),
$$
with zk attestations proving budget spend and purpose compliance.

### 6.3 Lineage and royalties

Reused CTV/A and model deltas reference **PLID**; royalties stream back to **nDATA-R** owners using Shapley-style approximations:

$$
\mathrm{Royalty}(X) = \sum_i \phi_i(X) \cdot r_i(t), \qquad 
\sum_i \phi_i(X) \approx 1.
$$
Royalty curves may decay (to encourage freshness) or step-up for high safety grade data.

### 6.4 Anti-sybil and quality

- **Per-robot DID + TEE evidence** prevents cost-free identity splits.  
- **Diversity threshold** (scene entropy, contact event variety) before minting a lot.  
- **Similarity hashing** and spot-audits penalise near-duplicates.

---

## 7. Learning from Lived Experience

### 7.1 μTokens and multimodal alignment

- **Vision:** masked autoencoding + contrastive alignment.  
- **Audio:** self-supervised embeddings (speech/environment).  
- **Tactile/force:** slip/contact patches with local dynamics.  
- **Proprioception:** predictive trajectory codes.

Alignment objective:

$$
\mathcal{L}_{\mathrm{align}} = -\mathbb{E}\left[\log \frac{\exp(\langle z_m, z_{m'} \rangle/\tau)}{\sum_j \exp(\langle z_m, z_j \rangle/\tau)} \right],
$$
with action-conditioned dynamics and skill distillation layered on.

### 7.2 Growth law (experience-driven)

Let $ M_R(t) $ be cumulative **licensable** μTokens derived from **nDATA-R**:

$$
\bar{\beta}(t) \propto M_R(t)^\gamma,\qquad 
M_R(t+\Delta) = M_R(t) + N(t)\, d \, \pi_{\mathrm{lic}},
$$
where $ d $ is daily μTokens/robot and $ \pi_{\mathrm{lic}} $ the licensable fraction. Then

$$
I(t) = \log N(t) \cdot M_R(t)^\gamma \cdot C(t).
$$
As evaluator ensembles improve and ALR-licensed coverage widens, $ C(t) \uparrow $, producing **super-linear** gains in effective capability.

---

## 8. Safety, Correctness, Privacy

- **PoI correctness:**
  $$
  P_{\mathrm{FA}} \le \varepsilon \quad \Rightarrow \quad q \ge \frac{\ln(1/\varepsilon)}{2(1/2-\theta)^2}.
  $$
- **CBC safety:** choose $ u $ to minimise $ \|u-u_{\mathrm{nom}}\|^2 $ subject to
  $$
  \frac{\partial h}{\partial x} \cdot (f+g u) + \alpha h(x) \ge 0
  $$
  alongside actuator/contact limits.  
- **PoA embodiment:** Merkle-ised sensor/actuation traces, CBC certificates; committee sampling; penalties for rejected segments.  
- **Privacy:** ALR + DP composition; zk attestations for budget use; **raw frames** remain local.

---

## 9. Market Clearing & Control

### 9.1 Prices and control

Dual-descent:

$$
p_R(t{+}1)=\max\bigl(0,\,p_R+\eta_p[D_R-\mathcal{U}_R]\bigr),\qquad
p_v(t{+}1)=\max\bigl(0,\,p_v+\eta_v[\psi-\psi^\*]\bigr).
$$
**MPC (mesh):** state $ y=[\rho_R,\rho_C,\rho_B,P_{\mathrm{FA}},\psi,\text{lat}] $; control $ u=[\psi,\lambda_{\mathrm{eff}},q,\theta,p_v,p_R] $; constraints $ \rho_k<1 $, $ P_{\mathrm{FA}}\le \varepsilon $, $ L_{\mathrm{tot}}\le L^\star $.  
**MPC (fleet):** include incident rate, battery, maintenance, nENERGY windows; require $ P_{\mathrm{unsafe}}\le \varepsilon_s $.

### 9.2 Throughput

$$
V_{\mathrm{emb}} \propto I \times \mathcal{U}_R \times (1 - P_{\mathrm{unsafe}}),\qquad 
S = S_{\mathrm{comp},R} \bigl(1+\chi\bigr) + S_{\mathrm{body}},\quad \chi=\frac{\psi}{1-\psi}.
$$

---

## 10. Data as a Real-World Asset (valuation & NAV)

### 10.1 Pricing a data lot

For lot $ D $ (nDATA-R), fair value:

$$
P(D) = \alpha \,\mathbb{E}[\Delta I(D)]
+ \beta \,\kappa_{\mathrm{cov}}(D)
+ \gamma \,\rho_{\mathrm{rare}}(D)
- \lambda_{\mathrm{risk}}\, \mathcal{R}(D),
$$
where **ΔI** is marginal information gain across reference tasks, **coverage** measures diversity (scenes/materials/language), **rarity** measures scarcity of events, and **risk** captures privacy/clean-up.

### 10.2 NAV and issuance (data tranches)

Group lots by modality mix and safety class.

$$
\text{NAV}_{\mathrm{nDATA\!-\!R}} = \sum_{D\in \text{tranche}} \mathrm{DCF}\big(P(D),\ \text{licence rate},\ \text{churn}\big) - \text{reserves}.
$$
Apply haircuts $ h_r $ for oracle variance, legal risk, and coverage volatility; cap issuance via $ \text{max\_supply} = \text{NAV}(1-h_r)/\text{unit\_value} $.

### 10.3 Royalty streams

Derivatives (models/CTV/A) share revenue with upstream **nDATA-R** owners per lineage and Shapley weights $ \phi_i(X) $; auditors sample lineage for correctness; disputes use zk proofs of ALR scope.

---

## 11. Token Supply & Emissions (token)

- **Genesis:** 1.00B $NEURO (illustrative).  
- **Allocation:** 15% contributors (4y), 15% treasury, 10% ecosystem grants, 10% market-making (18m), **35% operator/evaluator/data emissions** over 10y, 15% public/partners.  
- **Decay:** $ E_t = E_0 \cdot 2^{-t/H} $ with half-life $ H=24 $ months; configure a floor for long-run incentives.  
- **Burns:** fraction of verification fees and premium SLO mark-ups burned; inactivity slashing burned.  
- **cCOMP:** non-inflationary credit minted from attested on-robot time; floats vs $NEURO in a utilisation-aware AMM.

---

## 12. Revenue Model (protocol, operators, data owners)

### 12.1 Protocol inflows

- Base fees (τ to treasury).  
- Verification fees (share to evaluators + burn).  
- AMM spreads (cCOMP↔$NEURO).  
- RWA fees (listing/attestation/oracle).  
- **Data fees:** treasury share $ \tau_D $ from **nDATA-R** licences.  
- Buyback/burn policies configurable by governance.

### 12.2 Operator economics (per robot/day; illustrative)

$$
\mathrm{Rev}_{\mathrm{day}} \approx h \cdot (r_{\mathrm{clk}} P_c) \;+\; h \cdot \phi_v \;+\; \mathrm{royalty}_{\mathrm{CTV/A}} \;+\; L_{\mathrm{nDATA\!-\!R}},
$$
where $ h $ verified hours, $ r_{\mathrm{clk}} $ credits/hour, $ P_c $ cCOMP price, $ \phi_v $ verification fee intensity, and $ L_{\mathrm{nDATA\!-\!R}} $ data licensing revenue.  
Costs: energy $ C_e $, maintenance $ C_m $, insurance $ C_i $, verification burns $ C_v $, amortised capex $ C_a $.

### 12.3 Projections (directional, adjustable)

- **N (robots):** 1,200 → 3,600 → 9,000 (Y1→Y3).  
- **h (hours/day):** 6.2 → 7.0 → 8.1.  
- **$r_{\mathrm{clk}}$ (credits/h):** 1,050 → 1,250 → 1,480.  
- **$P_c$ ($NEURO/credit):** 0.0030 → 0.0036 → 0.0042.  
- **$ \phi_v $ ($NEURO/h):** 0.15 → 0.12 → 0.10.  
- **Data licensing:** 20 → 28 licensable lots/robot/day; average price 0.04 → 0.06 $NEURO; take-rate 35% → 45%.

**Fleet Y1 gross (ballpark):**  
$$
1{,}200 \times \bigl[6.2(1{,}050\cdot0.0030) + 6.2\cdot0.15 + 6.2\cdot0.02 + 0.28\bigr] \approx 1{,}200 \times 20.86 \approx 25{,}032\ \text{$NEURO/day$}.
$$
Treasury slice (assume 15% of a 25% fee base plus $ \tau_D=15\% $ on data fees) ≈ **~1.0k $NEURO/day**. Upside scales with $N$, $r_{\mathrm{clk}}$, premium SLOs, and data rarity premia.

**Sensitivity:**  
- $ \psi \uparrow \Rightarrow \chi \uparrow \Rightarrow $ throughput drops → raise prices or improve evaluators/zk.  
- Energy shocks → $ C_e \uparrow $; hedge with **nENERGY** windows.  
- Incident rate → $ C_i \uparrow $; reduce via CBC tuning, teleop policies, and safety-weighted matching.

---

## 13. Environmental Emissions (energy/CO₂e)

Per-robot daily energy and CO₂e:

$$
E_{\mathrm{day}} = P_{\mathrm{dev}} \cdot h,\qquad
\mathrm{CO2e}_{\mathrm{day}} = E_{\mathrm{day}} \cdot \kappa_{\mathrm{CO2}}.
$$
**Example:** $P_{\mathrm{dev}}=0.45\ \mathrm{kW},\, h=6.2,\, \kappa_{\mathrm{CO2}}=0.30\ \mathrm{kg/kWh} \Rightarrow E=2.79\ \mathrm{kWh},\ \mathrm{CO2e}=0.84\ \mathrm{kg}$ per robot/day.  
Shifting ≥50% hours to renewable windows ($\kappa\_{\mathrm{CO2}}\approx0.05$) via **nENERGY** can reduce intensity by \~42%.

---

## 14. Comparative Analysis (Bittensor-style networks and others)

| Dimension      | **NeuroMesh** (humanoid, on-robot)                                 | Bittensor-style (disembodied models)     |
| -------------- | ------------------------------------------------------------------ | ---------------------------------------- |
| Output         | **CTV/A** (thoughts + **actions**) with **PoA**                    | Text/image responses, gradients          |
| Compute        | **On-robot** (edge); $L_{\mathrm{net}}\approx 0$ for control                                | Remote miners; network latency tolerable |
| Safety         | **CBC**, human-aware envelopes, teleop policy                      | Not centred on embodied safety           |
| Verification   | PoI + **PoA**; optional zkML                                       | Peer scoring/bounties                    |
| RWA            | **nROBOT, nENERGY, nSTOR, nDATA, nDATA-R**                         | RWA optional                             |
| Data ownership | **Per-robot nDATA-R (DOC/PLID), ALR-scoped licensing & royalties** | Mixed, less formalised lineage/rights    |

**Conclusion:** knowledge markets vs capability markets. NeuroMesh prices **capability under constraints** and makes **data ownership** a tradable, enforceable RWA.

---

## 15. Governance, Policy, and Assurance

- **Weight:** $ W\_i = \omega\_1 \mathrm{stake}\_i + \omega\_2 \hat{r}\_i + \omega\_3 (p\_i/\bar{p}) + \omega\_4 \mathrm{agent\_contrib}\_i + \omega\_5 \mathrm{safety\_score}\_i + \omega\_6 \mathrm{data\_contrib}\_i $.
- **Parameters:** $ \psi^\*, q_{\min}, \theta $; haircuts $ h_r $; caps; redemption windows; ALR defaults; $ \varepsilon\_s $; data privacy reserve %.
- **Transparency:** publish parameter files, receipts/audits (hashes), incident post-mortems with remediation.
- **Security:** secure boot, sign-only OTA, TEE attestations; oracle medianisation with dispersion caps; circuit-breakers; slashing for misreporting.

---

## 16. Roadmap (humanoid- and data-aware)

- **0–6 months:** NeuroOS-H GA; PoI/PoA committees; on-robot cCOMP minting; **DOC/PLID**, **nDATA-R** lots; ALR lanes; receipts explorer.
- **6–12 months:** Data market beta (μToken lots); ΔI oracles; Shapley service; maintenance oracles; teleop pools; utilisation-aware pricing.
- **12–18 months:** Royalty streaming for CTV/A; zkML queues (sensitive domains); premium SLOs; insurer-grade audit packs.
- **18–24 months:** Regional clusters; cross-market routing; nDATA-R and nROBOT refinancing lanes; RWA basket indices.
- **24–36 months:** Export-aware data bundles; expanded social-policy libraries; marketplace analytics and credit curves.

---

## 17. Risks, Limitations, and Open Questions

- **zkML proof costs** (large circuits). Mitigation: selective zk in high-stakes queues.
- **Sim-to-real drift.** Mitigation: μToken diversity; evaluator ensembles; periodic ground-truthing.
- **HRI risk.** Mitigation: CBC envelopes, teleop triggers, safety class certification.
- **Regulatory heterogeneity.** Mitigation: ALR defaults by region; auditor packs.
- **Economic cyclicality.** Mitigation: haircuts, issuance caps, circuit breakers, reserves.
- **Fair ΔI estimation.** Ongoing research: robust surrogates and dispute resolution.

---

## 18. Conclusion

NeuroMesh is an **intelligence layer** for **fully customisable humanoids** that scales into a **decentralised superbrain** as robots perceive the world. It treats compute, capability, and—decisively—**data** as assets with **ownership, rights, valuation, and rewards**. By enforcing correctness and safety on-device, and settling rights and revenues on-chain, the network compounds like a living organism: every safe, attested minute deepens memory, broadens skill, and strengthens the economy.

---

## Appendix A — Key Equations

1. **PoI quorum**
   $$
   q \ge \frac{\ln(1/\varepsilon)}{2(1/2-\theta)^2}.
   $$
2. **Overhead**
   $$
   \chi = \frac{\psi}{1-\psi}, \qquad S = S_{\mathrm{comp},R}\bigl(1+\chi\bigr) + S_{\mathrm{body}}.
   $$
3. **Queueing**
   $$
   W \approx \frac{\rho_R}{\mu_R-\lambda_R}, \qquad \mu_R = \frac{1}{\mathbb{E}[S_{\mathrm{comp},R}]}.
   $$
4. **CBC**
   $$
   \frac{\partial h}{\partial x} \cdot (f + g u) + \alpha h(x) \ge 0.
   $$
5. **Intelligence density**
   $$
   I = \log N \cdot \bar{\beta} \cdot C.
   $$
6. **Throughput**
   $$
   V_{\mathrm{emb}} \propto I \times \mathcal{U}_R \times \bigl(1 - P_{\mathrm{unsafe}}\bigr).
   $$
7. **DP composition**
   $$
   \varepsilon_{\mathrm{total}} \le \sqrt{2T\ln(1/\delta)}\,\bar{\varepsilon} + T\,\bar{\varepsilon}\,\bigl(e^{\bar{\varepsilon}}-1\bigr).
   $$
8. **Data price**
   $$
   P(D) = \alpha \,\mathbb{E}[\Delta I] + \beta \,\kappa_{\mathrm{cov}} + \gamma \,\rho_{\mathrm{rare}} - \lambda_{\mathrm{risk}}\,\mathcal{R}.
   $$
9. **Emissions**
   $$
   E_{\mathrm{day}} = P_{\mathrm{dev}} h, \qquad \mathrm{CO2e} = E_{\mathrm{day}} \kappa_{\mathrm{CO2}}.
   $$
10. **Emissions (token)**
    $$
    E_t = E_0 \cdot 2^{-t/H} \quad \text{(10-year pool)}.
    $$

---

## Appendix B — Worked Scenarios (brief)

- **Retail front-of-house:** wayfinding, safe handovers; dialogue PoA; ALR excludes face ID; CTV/A reused by other venues (royalties).
- **Micro-fulfilment:** deformables bin-picking with tactile slip recovery; night learning in **nENERGY** windows; nDATA-R lots priced by rarity of materials.
- **Industrial inspection:** valve torque envelopes; evaluator ensembles; maintenance oracles update risk; insurance priced off PoA history.
- **Event logistics:** lift–carry with human proximity envelopes; teleop overrides logged; Shapley splits across perception/planning/control.

---

## Appendix C — Governance Surfaces (suggested defaults)

- $ \psi^\* \in [0.10,0.18] $, $ q_{\min} \in [7,11] $, $ \theta \in [0.60,0.67] $.

- Safety cap $ \varepsilon_s \in [10^{-4},10^{-3}] $ per episode depending on class.
- Haircuts $ h\_r $: nDATA-R 20–40% (jurisdiction and variance dependent), nROBOT 10–25%, nENERGY 5–15%, nSTOR 5–10%.
- Privacy reserve: 5–10% of data fees to fund redaction/cleanup after policy changes.

---

## Appendix D — Practical Integration Notes

- **Install intelligence layer:** NeuroOS-H, choose pre-audited skills, set CBC envelopes; enable receipts by default.
- **Tokenise data:** turn on **DOC/PLID** generation; configure ALR defaults; mint **nDATA-R** lots by time window/site.
- **Operate to earn:** schedule jobs, align heavy learning with **nENERGY** windows, list μToken lots; monitor dashboards for $ \rho\_R, \psi, P\_{\mathrm{unsafe}} $, evaluator accuracy, reuse ratios, ΔI leaders.
- **Evolve:** adopt new evaluator ensembles, enable zk for premium queues; expand royalty participation through iCTVs and nDATA-R tranches.

---

*End of document.*
