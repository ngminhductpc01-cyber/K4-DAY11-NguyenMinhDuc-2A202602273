# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_152940.jpg
- L1+R4+M6: LRM (center)
- L4+R3: LR_noM (center)
- L2+R2+M2: LRM (center)
- L3+R5+M9: LRM (mid)
- L5+R1+M1: LRM (mid)
- R6: R_only (mid)
- M3: M_only (edge)
- M4: M_only (mid)
- M7: M_only (center)
- M8: M_only (center)
## adasind_167700.jpg
- L7+R8+M9: LRM (center)
- L1+R3+M3: LRM (mid)
- L6+R7: LR_noM (center)
- L9+R6: LR_noM (edge)
- L4+R2+M7: LRM (mid)
- L2+R1+M1: LRM (center)
- L10+R5+M6: LRM (center)
- L8+R9: LR_noM (mid)
- L5: L_only (center)
- R4+M4: RM_noL (center)
- M5: M_only (mid)
- M8: M_only (mid)
## adasind_212280.jpg
- L3+R3: LR_noM (edge)
- L4+R2+M2: LRM (center)
- L2+R1: LR_noM (center)
- L1+M3: LM_noR (mid)
- L5+M1: LM_noR (center)
- M5: M_only (edge)
- M6: M_only (edge)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 6 | 3 | 1 | 1 | 1 | 0 | 2 |
| mid | 4 | 1 | 1 | 0 | 0 | 1 | 3 |
| edge | 0 | 2 | 0 | 0 | 0 | 0 | 3 |
