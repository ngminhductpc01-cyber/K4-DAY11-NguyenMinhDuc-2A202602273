# P5 independent recheck — version 2

Recheck source: exported XMLs, original images, P3 QA screenshots and the
approved handoff. Parking was deliberately excluded: the user supplied the
final Parking annotation and Job 53 was confirmed read-only.

| Scope | Finding / decision | Recheck result |
|---|---|---|
| C0 Job 54 | Missing R2 Bike | Fixed in `exports/c0-v2.zip`; box `(426.94,736.53)-(535.71,910.15)` present. |
| C0 Job 54 | Missing R3/R5/R6 ThreeWheeler | Fixed; all three boxes present in `exports/c0-v2.zip`. |
| B3 152940 | Below-H L3 Bike; missing ThreeWheeler | Fixed; small Bike removed and ThreeWheeler `(182.05,811.03)-(217.52,853.15)` added. |
| B3 167700 | L5 Truck class | Fixed; same box is `Car` in v2. |
| B3 212280 | Duplicate L5 Bike | Fixed; v2 has one retained Bike (L2) and no duplicate L5. |
| B3 212280 | Bus L3 truncated | Fixed; v2 Bus has `truncated=true`. |

`py lab11.py rework` reports center-slice missing `1→0` and spurious `2→0`.
Its L2+R1 row is marked non-applicable because the retained Pedestrian+Bike pair
was intentionally not changed; that is consistent with R03 and P4-06.

Remaining escalations are not rework defects: the teaching-reference R1/R03
disagreement and the historic `r1_craft` lock-code mismatch remain documented in
the escalation ticket and decision log. The active rework lock is `F6A8-6EF7`.
