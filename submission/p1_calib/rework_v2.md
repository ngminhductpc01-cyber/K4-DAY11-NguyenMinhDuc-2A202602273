# C0 calibration — version 2 evidence

Rework was applied only to CVAT Job 54 (`adasind_019560.jpg`). The export is
`exports/c0-v2.zip`. The original P1 locked artifact was retained unchanged; no
`lock calib` command was run because that would replace the baseline evidence.

| Finding | v2 action | Verified v2 box |
|---|---|---|
| R2 Bike missing | Added | `(426.94,736.53)-(535.71,910.15)` |
| R3 ThreeWheeler missing | Added | `(39.96,772.09)-(98.53,849.49)` |
| R5 ThreeWheeler missing | Added | `(326.53,721.89)-(456.23,849.49)` |
| R6 ThreeWheeler missing | Added | `(286.79,742.80)-(339.08,824.38)` |

XML parsing of the v2 export confirms six boxes on the frame: three Bike and
three ThreeWheeler. This is an export/review record, not a replacement for P1.
