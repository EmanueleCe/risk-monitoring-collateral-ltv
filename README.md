# Lombard Lending Risk & Stress Testing Model

![LTV Dynamics – Severe Stress Scenario](images/LTV_Dynamics_Under_Severe_Scenario.png)

This project analyses the risk dynamics of a Lombard loan backed by a diversified collateral portfolio, focusing on how the loan-to-value (LTV) evolves over time and reacts to adverse market conditions.

The model does not aim to price the loan, forecast markets or assess borrower creditworthiness. It focuses instead on collateral-driven risk monitoring, in line with how Lombard structures are typically managed within private banking and risk functions.

The project addresses a practical question: how resilient a Lombard loan structure is under market stress, and under which conditions margin calls or liquidation events become relevant.


## Project Overview

The analysis is structured as a sequence of notebooks, each building progressively on the previous one. This follows a production-style workflow, where assumptions are defined upfront, core mechanics are implemented first, and stress testing is performed only after baseline behaviour is well understood.

The initial notebooks focus on preparing historical price data and defining the key assumptions of the structure, including collateral composition, haircuts and risk thresholds. These assumptions remain fixed throughout the project to isolate market-driven effects.

Once the assumptions are set, the collateral engine is built by computing market values, applying haircuts and deriving the eligible collateral value on a daily basis. This allows for the calculation of the loan-to-value ratio over time, which represents the central risk metric of the model.

Risk escalation is then introduced through explicit margin call and liquidation rules. Rather than relying on static snapshots, the model tracks these events dynamically across time, highlighting when and for how long the structure would breach predefined thresholds.


## Stress Testing Approach

Stress testing is performed by applying deterministic shocks on top of the historical price path, within clearly defined stress windows. The objective is to assess how the Lombard structure would have behaved if market conditions had deteriorated further during known stress periods, without rewriting historical price dynamics.

Three stress scenarios are analysed. The first focuses on an equity-driven shock during the most acute phase of the COVID sell-off. The second represents a prolonged credit stress environment inspired by the tightening financial conditions observed in 2022. The third scenario combines severe equity and bond shocks and is explicitly designed as a worst-case liquidation test.

Across all scenarios, the loan amount, collateral composition and haircuts remain unchanged. Only asset prices are shocked, ensuring that the results reflect market stress rather than structural changes to the deal.

The stressed LTV trajectory is compared against the baseline, with results summarised in a concise scenario table highlighting maximum LTV levels, margin call breaches and liquidation events.

## Key Insights

The analysis highlights the importance of conservative initial structuring in Lombard lending risk management. Under baseline conditions and moderate stress scenarios, the loan remains resilient, even during historically severe market episodes.

Equity drawdowns emerge as the primary driver of short-term risk escalation, while bond stress becomes more relevant in prolonged tightening environments where diversification benefits weaken. Only under severe combined tail scenarios does liquidation risk materialise, confirming the role of margin calls as an effective early-warning mechanism rather than a frequent trigger.

Overall, the project illustrates how disciplined collateral design, combined with transparent monitoring and stress testing, can materially reduce forced liquidation risk while preserving risk visibility under extreme conditions.


## Future Extensions

Several extensions are intentionally left out of the current version to preserve clarity and focus. Potential future developments include probabilistic stress testing via Monte Carlo simulation, dynamic margining and collateral top-up logic, and more advanced early-warning indicators based on LTV dynamics.

These enhancements represent a possible next step, but are intentionally excluded from the current version to keep the framework focused on realistic and interpretable risk management practices.

## Disclaimer

This project is for educational and illustrative purposes only and does not constitute investment advice or a production trading system.
