# Connection–Delivery Scaling, Decoupling and Metering Responsiveness of Nigerian Electricity Distribution Companies

## Overview

This repository contains the data-processing, statistical, econometric, clustering, structural-break, and visualisation workflow for the study of electricity connection expansion and billed electricity delivery across Nigeria's electricity Distribution Companies (DISCOs).

The study examines whether growth in customer connections translates proportionately into growth in billed electricity delivery. It distinguishes the **extensive margin** of electricity access from the **intensive margin** of electricity delivery and evaluates the role of metering penetration in shaping this relationship.

The analysis covers the 11 Nigerian DISCOs using a monthly panel from **January 2015 to December 2023**.

---

## Research Questions

### RQ1 — Connection–delivery scaling

Does expansion in customer connections translate proportionately into billed electricity delivery?

### RQ2 — Access–delivery decoupling

How frequently, severely, and persistently does customer-connection growth diverge from billed electricity delivery growth?

### RQ3 — Metering–delivery association

What is the short-run association between changes in metering penetration and billed electricity delivery intensity after accounting for dynamic persistence and common cross-sectional influences?

### RQ4 — DISCO heterogeneity and regimes

How heterogeneous is the metering–delivery relationship across DISCOs, and can DISCOs be distinguished into empirically different connection–delivery regimes?

### RQ5 — Structural change

Does the metering–delivery relationship exhibit nonlinear or structurally changing behaviour over the study period?

---

## Data

The analytical panel contains:

* 11 Nigerian DISCOs
* Monthly observations
* January 2015–December 2023
* 1,188 DISCO-month observations before derived-variable sample restrictions

### DISCOs

* Abuja
* Benin
* Eko
* Enugu
* Ibadan
* Ikeja
* Jos
* Kaduna
* Kano
* Port Harcourt
* Yola

### Core source variables

* Total customers
* Metered customers
* Estimated customers
* Energy billed (GWh)
* Revenue collected (million NGN)

### Derived variables

Let:

$$
C_{it} = \text{total customers}
$$

$$
M_{it} = \text{metered customers}
$$

$$
U_{it} = \text{estimated customers}
$$

$$
G_{it} = \text{energy billed}
$$

The principal analytical variables are:

$$
MR_{it}=\frac{M_{it}}{C_{it}}
$$

$$
UR_{it}=\frac{U_{it}}{C_{it}}
$$

$$
EDI_{it}=\frac{G_{it}}{C_{it}}
$$

$$
y_{it}=\ln(EDI_{it})
$$

---

## Analytical Framework

### Extensive margin

The extensive margin is customer-connection growth:

$$
\Delta\ln C_{it}
$$

It measures changes in the size of the connected customer base.

### Intensive margin

The intensive margin is billed electricity delivery per customer:

$$
\Delta\ln EDI_{it}
$$

It measures changes in billed electricity delivered relative to the number of connected customers.

### Growth decomposition

The study uses the identity:

$$
\Delta\ln G_{it}
=
\Delta\ln C_{it}
+
\Delta\ln EDI_{it}
$$

This separates changes in billed electricity growth into extensive and intensive components.

### Access–Delivery Decoupling Index

$$
ADDI_{it}
=
\Delta\ln G_{it}
-
\Delta\ln C_{it}
$$

Therefore:

$$
ADDI_{it}
=
\Delta\ln EDI_{it}
$$

A negative ADDI indicates that customer-connection growth exceeds the growth of billed electricity delivery per customer. It does **not** by itself establish unmet demand, disconnection, or service unreliability.

---

## Econometric Strategy

The econometric analysis follows a staged design.

### 1. Cross-sectional dependence

Cross-sectional dependence is assessed using the **Pesaran CD test**.

This establishes whether DISCOs can be treated as cross-sectionally independent.

### 2. Integration properties

The **Cross-sectionally Augmented IPS (CIPS)** framework is used to assess stationarity while allowing for cross-sectional dependence.

The final integration evidence indicates:

* \(\ln(EDI)\): \(I(0)\)
* \(MR\): nonstationary in levels
* \(\Delta MR\): \(I(0)\)

Because the level variables do not form a conventional jointly \(I(1)\) system, a conventional \(I(1)\)-\(I(1)\) long-run cointegration/PMG framework is not imposed.

### 3. Fixed-effects benchmark

A DISCO fixed-effects model is estimated as a benchmark:

$$
\ln(EDI_{it})
=
\alpha_i
+
\beta\Delta MR_{it}
+
\varepsilon_{it}
$$

### 4. Lag-augmented CCE-MG

The preferred model is a dynamic **Common Correlated Effects Mean Group (CCE-MG)** specification.

The model is:

$$
y_{it}
=
\alpha_i
+
\rho_i y_{i,t-1}
+
\beta_i\Delta MR_{it}
+
\sum_{p=0}^{4}\gamma_{ip}\bar y_{t-p}
+
\sum_{p=0}^{4}\delta_{ip}\overline{\Delta MR}_{t-p}
+
\varepsilon_{it}
$$

where the cross-sectional averages proxy unobserved common factors.

The model contains:

* one lag of the dependent variable;
* current metering change;
* current cross-sectional averages;
* four lags of the relevant cross-sectional averages.

---

## Heterogeneity and Regime Analysis

DISCO-specific CCE-MG coefficients are used to assess heterogeneity.

The regime feature matrix contains:

* Mean metering ratio
* Mean delivery intensity
* Mean ADDI
* ADDI persistence
* DISCO-specific metering–delivery coefficient

Features are standardised before K-means clustering.

Candidate solutions for:

$$
K=2,\;3,\;4
$$

are evaluated using:

* Silhouette score
* Calinski–Harabasz index
* Davies–Bouldin index
* Cluster size
* Repeated-initialisation stability

The final analysis retains a **three-regime solution** based on stability, non-singleton structure, and substantive differentiation.

---

## Structural-Break Analysis

The structural-change analysis searches for a common break across an interior period of the sample.

### Search window

**July 2016–August 2022**

The boundary trimming avoids candidate dates too close to the beginning or end of the sample and ensures adequate observations on both sides of each candidate date while accommodating the lag structure of the model.

The search contains **74 candidate monthly break dates**.

The selected break is identified using a Wald-type structural-break screen and validated using a Bonferroni-adjusted significance criterion.

---

## Principal Findings

### RQ1

Customer connections increased across the DISCOs while billed electricity delivery intensity declined on average. The evidence therefore rejects a simple proportional scaling interpretation between connection expansion and billed electricity delivery.

### RQ2

Negative ADDI episodes are recurrent and heterogeneous across DISCOs. Decoupling varies considerably in frequency, magnitude, and persistence.

### RQ3

The preferred lag-augmented CCE-MG model produces a positive and statistically significant average association:

$$
\bar{\beta}=0.704622
$$

$$
SE=0.206186
$$

$$
p=0.006576
$$

$$
95\%\,CI=[0.245212,\;1.164032]
$$

The mean persistence parameter is:

$$
\bar{\rho}=0.742875
$$

DISCO-specific coefficients range from:

$$
-0.460530
$$

to:

$$
2.017378
$$

Ten of eleven DISCO-specific coefficients are positive, while four are statistically significant at the 5% level.

The residual diagnostics indicate that CCE adjustment substantially reduces cross-sectional dependence, although statistically significant residual dependence remains. Ljung–Box tests provide no evidence of pervasive residual serial correlation at 12 lags.

### RQ4

Three empirical connection–delivery regimes are identified:

#### Regime 0 — Lower Metering–Delivery Performance

**Enugu, Jos, Kaduna, Kano, Yola**

#### Regime 1 — Higher Metering–Delivery Intensity

**Benin, Eko, Ikeja**

#### Regime 2 — High Metering–Delivery Responsiveness

**Abuja, Ibadan, Port Harcourt**

The regimes differ across metering penetration, delivery intensity, ADDI behaviour, persistence, and metering–delivery responsiveness.

### RQ5

The structural-break search identifies:

$$
\boxed{\text{May 2018}}
$$

as the strongest candidate break.

$$
W=26.494
$$

$$
p=2.6\times10^{-7}
$$

with:

$$
\Delta\beta=0.986352
$$

The Bonferroni-adjusted criterion is:

$$
\alpha_B
=
\frac{0.05}{74}
=
6.76\times10^{-4}
$$

The average pre-break coefficient is:

$$
0.156244
$$

while the post-break coefficient is:

$$
0.839995
$$

giving:

$$
\Delta\bar{\beta}=0.683751
$$

Eight DISCOs experience increases and three experience decreases. The paired t-test and Wilcoxon signed-rank test do not reject equality of pre- and post-break coefficients at conventional levels. The evidence therefore supports a **system-level structural transition with heterogeneous DISCO-level adjustment**, rather than a uniform coefficient shift.

---

## Reproducibility and Data Integrity

The workflow includes explicit validation checkpoints for:

* panel dimensions;
* DISCO count;
* date continuity;
* duplicate DISCO-date observations;
* missing values;
* variable types;
* derived-variable identities;
* decomposition identity;
* ADDI identity;
* estimation samples;
* residual diagnostics.

Known source-data omissions are retained as missing values and are **not imputed**.

In particular, the missing December 2023 metering components for Kano are treated as a genuine source-data gap.

---

---

## Principal Outputs

### RQ1

* Extensive versus intensive growth-margin figure
* Customer-growth versus billed-energy-growth figure
* Decomposition validation table

### RQ2

* ADDI summary table
* Negative-episode statistics
* ADDI trajectory plots

### RQ3

* Integration diagnostics
* FE benchmark
* CCE-MG summary
* DISCO-specific coefficient plot
* Residual cross-sectional correlation heat map
* Residual diagnostics

### RQ4

* K-selection diagnostics
* Regime-profile heat map
* Regime profile table
* DISCO regime assignment

### RQ5

* Structural-break search plot
* Pre/post coefficient comparison
* Structural-break validation
* Regime-level structural-change summary

---

## Interpretation Principles

The study deliberately distinguishes **association from causation**.

The estimated CCE-MG coefficients are interpreted as conditional short-run associations between changes in metering penetration and billed electricity delivery intensity. They are not interpreted as causal treatment effects.

Similarly, negative ADDI is interpreted as **connection–delivery divergence**, not direct proof of unmet electricity demand.

---

## Limitations

### Cross-sectional dependence

Residual cross-sectional dependence remains after CCE adjustment.

**Mitigation:** Common Correlated Effects estimation, cross-sectional-average lags, and explicit residual-dependence diagnostics.

### Small cross-sectional dimension

The study contains 11 DISCOs.

**Mitigation:** conservative interpretation, explicit DISCO-level reporting, clustering stability checks, and avoidance of unnecessarily complex higher-dimensional specifications.

### Source-data omission

Kano has a December 2023 omission in metering components.

**Mitigation:** no imputation; the observation is retained as missing and excluded only where required by the relevant estimator.

### Observational design

The panel does not establish causality.

**Mitigation:** results are framed as associations, while dynamic persistence, common cross-sectional influences, integration properties, and structural changes are explicitly modelled and tested.

---

## Computational Environment

The analysis is implemented primarily in Python using:

* Python
* pandas
* NumPy
* SciPy
* statsmodels
* scikit-learn
* matplotlib
* seaborn
* openpyxl
* Jupyter Notebook

---

## Reproducibility

To reproduce the analysis:

1. Place the permitted raw dataset in `data/raw/`.
2. Install the required Python packages.
3. Run the notebooks sequentially.
4. Preserve the stated notebook order because later RQ analyses depend on validated objects generated by earlier stages.
5. Generated tables and figures are saved to `outputs/tables/` and `outputs/figures/`.

The notebooks are intentionally organised around short, auditable computational blocks, with validation, critical results, visualisations, and exports retained at each stage.

---

## Citation

This repository accompanies the research manuscript on connection–delivery scaling, access–delivery decoupling, metering responsiveness, and structural heterogeneity across Nigerian electricity DISCOs.

**Manuscript Tentative Title:** *ENERGY BILLING INTENSITY AND CUSTOMER-CONNECTION EXPANSION IN A FRONTIER MARKET ECONOMY: A CASE STUDY OF NIGERIA’S ELECTRICITY DISTRIBUTION SECTOR ![Uploading image.png…]()
*
**Corresponding Author:** OFFORSON GOLDEN CHIBUEZE
**Year:** 2026

---

## Status

**Analysis status:** Complete
**Panel period:** January 2015–December 2023
**DISCOs:** 11
**Primary econometric estimator:** Lag-augmented CCE-MG
**Regime solution:** K = 3
**Structural break:** May 2018
**Reproducibility notebook:** Complete

