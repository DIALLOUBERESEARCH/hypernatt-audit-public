# 671 - Engine release and research pipeline

Published: 2026-09-14T23:15:00Z. Operator-authored, dated evidence summary.
This is not an independent audit or a statement of expected returns.

## Release and operational boundary

The proprietary HyperNatt engine candidate F331 was integrated in F332,
commit ca79b0ab, and deployed at 23:12 UTC on 14 September 2026.
The paper service and the vault execution service use a common decision
source and configuration. Their operational identities matched after deployment.
Real execution still depends on available liquidity, fees and confirmed fills;
shared decision code does not promise identical paper and real results.

At 23:15 UTC, vault entries and execution were disabled, with no open position
or open order. Activation is the owner's decision. This statement is a dated
observation, not a continuous assertion of safety. The paper history survived
the restart: all 78 previously closed cycles were retained.

## What changed

Entry admission and position management were integrated into the common
decision path. Additional exit decisions use confirmed execution handling.
Existing protective exits retain priority. Software checks cover restart,
state restoration, historical replay and the boundary with order execution.

Immediate operational checks passed. Prolonged operational validation and
prospective financial evaluation are separate steps. A running deployment
is not evidence of a profitable strategy.

## Limits of the candidate evidence

The candidate was selected after examining the same three trades used in its
development comparison. This is a small, post-hoc sample, not unseen evidence.
On the fixed replay sample, modeled net account changes per 1,000 initial units
were +0.752938 under recorded quotes and base modeled fees, +0.932954 under
the alternative taker-cost model, and -7.105249 under higher stressed costs.
Exit timing changes between these scenarios; these are not fixed trades with
only a fee subtraction. The stress scenario remains negative.
The paper-price observations used here came from Binance Spot, not real
Hyperliquid fills. No positive future expectation has been established.

## Research and calibration loop

1. Preserve source observations and provenance. The independent native
   Hyperliquid recorder continues collecting without engine modifications.
2. Record decision inputs, versions, configuration and state in a replayable film.
3. Compare a frozen reference with a candidate in the test bench, including
   costs, execution uncertainty, drawdowns and failures.
4. Validate implementation and restart behavior before a controlled deployment.
5. Evaluate future observations under a separately fixed financial protocol.
   A new engine version requires a new evaluation period and explicit criteria.
6. Return weaknesses to the workshop. Keep failed hypotheses and their limits.

Historical studies and prior deployment cohorts remain archives. In particular,
the positive candle-close absorption statistic was affected by look-ahead
selection and does not establish an executable pre-close edge. Native order
book data may help test this question; collecting it does not guarantee success.

## Reading the public page

The trade table is paper history spanning multiple engine versions. Its reported
per-trade gain follows the journal convention and can exclude entry fees. The
realized account PnL is shown separately and uses the source's initial capital.
Do not interpret mixed history as the candidate's net expectation.
If the telemetry source is unavailable or malformed, the API returns unavailable
and the page does not substitute invented trades or a historical win rate.
Ledger publication time is a fixed date, not a live verification clock.
Public note fingerprints allow byte verification; they do not certify conclusions.

Six older ledger fingerprints were corrected to match the already served
Linux line endings. The archived note contents were not changed.
