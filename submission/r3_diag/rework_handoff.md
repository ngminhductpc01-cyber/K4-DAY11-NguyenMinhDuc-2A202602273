# Rework handoff to A — version 2 not yet created

Owner for every item: Nguyễn Minh Đức (A). Work must be done only in the future version-2 CVAT session after the team authorizes rework.

1. **Frame:** adasind_152940.jpg  
   **Object:** L3 (`Bike`, `(256.00,830.88)–(265.91,851.66)`)  
   **Current state:** A 21 px-high Bike box is present.  
   **Problem:** It is below the R01 H=40 inclusion threshold.  
   **Evidence:** `submission/screenshots/r2_qa_adasind_152940_L3.png`.  
   **Required change:** Remove L3 after confirming the same measurement on the original image.  
   **Expected result:** No below-threshold box remains.

2. **Frame:** adasind_152940.jpg  
   **Object:** missing ThreeWheeler at reference location R6, approximately `(183,810)–(218,853)`.  
   **Current state:** No learner box.  
   **Problem:** A visible vehicle above H=40 is absent.  
   **Rule:** R04, R01.  
   **Evidence:** `r1_craft/compare.md`, original image, and teaching reference (opened only after P3).  
   **Required change:** Add one tight `ThreeWheeler` box around the visible object on the original fisheye image.  
   **Expected result:** One valid in-scope ThreeWheeler; no replacement with Bus/Truck.

3. **Frame:** adasind_167700.jpg  
   **Object:** L5 (`Truck`, approximately `(584,876)–(702,1003)`)  
   **Current state:** Passenger vehicle labelled Truck.  
   **Problem:** Image and L/R/M comparison support `Car`, not Truck.  
   **Rule:** R04.  
   **Evidence:** `r3_diag/local_quality_conflicts.csv`, IoU 0.928 against reference Car.  
   **Required change:** Change L5 class to `Car`; keep its tight visible geometry.  
   **Expected result:** Car classification, with no new box.

4. **Frame:** adasind_212280.jpg  
   **Object:** L5 (`Bike`, `(304,909)–(369,1045)`)  
   **Current state:** Nearly identical to L2.  
   **Problem:** Duplicate of a single physical bicycle.  
   **Rule:** R01.  
   **Evidence:** `submission/screenshots/r2_qa_adasind_212280_L2_L5.png`.  
   **Required change:** Remove L5 and retain L2 as the bike component of the R03 Pedestrian + Bike pair.  
   **Expected result:** Exactly one Bike box for that bicycle; retain L1 Pedestrian.

5. **Frame:** adasind_212280.jpg  
   **Object:** L3 (`Bus`, `(0,761)–(136,1104)`)  
   **Current state:** `truncated=false`.  
   **Problem:** The visible bus is cut by the left image/lens boundary.  
   **Rule:** R05.  
   **Evidence:** `submission/screenshots/r2_qa_adasind_212280_L3.png`.  
   **Required change:** Set `truncated=true`; do not change Bus class or geometry unless a direct visual check shows another issue.  
   **Expected result:** Truncation attribute reflects the visible boundary cut.

## Escalated, not rework

- adasind_212280.jpg reference R1 represents the walking person plus bicycle as one Bike. The learner L1 Pedestrian + L2 Bike follows R03 and is retained pending reference review.
- The lock-code mismatch remains pending verification. Do not relock, change XML, or create any v2 export to resolve it.
