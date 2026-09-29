# Escalation ticket

## Ticket 1

- **Frame:** adasind_212280.jpg
- **Ảnh chụp:** `submission/screenshots/r2_qa_adasind_212280_L2_L5.png`
- **Expected impact:** Reference R1 treats a person visibly walking a bicycle as a single Bike. If accepted blindly, this would obscure the required R03 Pedestrian + Bike distinction and distort learner/reference comparison in the center zone.
- **Owner:** qa
- **Recommendation:** Lab QA should review R1 on the original image and correct/reference-note it if the person is confirmed to be walking rather than riding. Retain learner L1 Pedestrian + L2 Bike unless that image review disproves it.

## Ticket 2

- **Frame:** B3-center slice (lock artifact; no single object frame)
- **Ảnh chụp:** `submission/screenshots/r2_qa_adasind_212280_L3.png` records the reviewed locked artifact context; it is not evidence that changes the lock.
- **Expected impact:** The recorded r1_craft lock-code mismatch cannot be treated as verified before final submission.
- **Owner:** qa
- **Recommendation:** Verify the provenance of the original export and recorded lock outside this review. Do not modify `lock.txt`, XML, or create/relock a v2 export to force agreement.
