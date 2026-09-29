# QA review · B3-center

Reviewer: Nguyễn Lâm Bách
Role: B · QA độc lập
Annotator: Nguyễn Minh Đức
Slice: B3-center
Annotation commit: 1947a5a
Lock recorded: 4B05-4C53
Lock verification: pending — code mismatch detected

QA performed visually against image + guideline; automated lock verification pending due to lock-code mismatch.

## Scope and method

Reviewed all three frames in the existing CVAT job in view-only use, cross-checked against the locked `annotations.xml`, the original fisheye images, and rules `R01`–`R09`. No teaching reference, model output, worked example, or comparison report was opened during this review. No annotation was edited or saved.

## Frame review

### adasind_152940.jpg

Frame: adasind_152940.jpg
Object ref: L3
Current class: Bike
Rule ID: R01
Observation: The current rectangle is `(256.00, 830.88)–(265.91, 851.66)`, so its visible height is about 21 px. The original fisheye image shows only this small distant two-wheeler at this location.
QA concern: A box is present although the object is below the H=40 px inclusion threshold.
What should be checked: Re-measure against the original image and remove the box if the visible height remains below 40 px.
Evidence: `submission/screenshots/r2_qa_adasind_152940_L3.png`; locked XML coordinates above.

All other visible ≥40 px road users and the ego-body/lens-border areas were reviewed. No additional finding had enough visual evidence to record in this frame.

### adasind_167700.jpg

Frame: adasind_167700.jpg
Object ref: L1–L10
Current class: mixed (`Pedestrian`, `Bike`, `Truck`, `ThreeWheeler`)
Rule ID: R03, R04, R05, R06, R07, R08
Observation: The two people walking their bicycles are represented as separate pedestrian/bike pairs; the left auto-rickshaw is labelled `ThreeWheeler`; ego body and two lens-border ignore polygons are present.
QA concern: No specific error is sufficiently supported by the blind visual review.
What should be checked: Preserve these assignments unless later diagnosis produces image-and-rule evidence to the contrary.
Evidence: Original `assets/images/adasind_167700.jpg`, existing CVAT object list, and locked XML.

### adasind_212280.jpg

Frame: adasind_212280.jpg
Object ref: L2 + L5
Current class: Bike + Bike
Rule ID: R01
Observation: L2 is `(304, 909)–(369, 1044)` and L5 is `(304, 909)–(369, 1045)`; both cover the same bicycle.
QA concern: Duplicate box for one object.
What should be checked: Confirm the two IDs refer to one physical bicycle, then retain one correctly sized `Bike` box only.
Evidence: `submission/screenshots/r2_qa_adasind_212280_L2_L5.png`; locked XML coordinates.

Frame: adasind_212280.jpg
Object ref: L3
Current class: Bus
Rule ID: R05
Observation: The bus rectangle starts at `xtl=0.00`; the visible vehicle is cut at the left image/lens boundary, while the current attribute is `truncated=false`.
QA concern: Truncation attribute appears inconsistent with the visible fisheye boundary.
What should be checked: Verify the visible cut is the image/lens boundary (rather than occlusion by another object) and set `truncated=true` if confirmed.
Evidence: `submission/screenshots/r2_qa_adasind_212280_L3.png`; locked XML and original image.

Frame: adasind_212280.jpg
Object ref: L4
Current class: Bike
Rule ID: R03, R05
Observation: The right-side motorcycle is separately boxed; it is not a rider-plus-vehicle split.
QA concern: No specific error is sufficiently supported by the blind visual review.
What should be checked: Preserve unless later image evidence identifies a geometry or attribute issue.
Evidence: Original `assets/images/adasind_212280.jpg`, existing CVAT object list, and locked XML.

## QA closure

- Frames reviewed: 3/3 (`adasind_152940.jpg`, `adasind_167700.jpg`, `adasind_212280.jpg`)
- Findings with sufficient visual evidence: 3
- Screenshots: 3
- Unresolved: Lock-code mismatch pending verification; no automated lock result is claimed.
- Blind QA confirmed: Yes — reference/model/worked material was not used before this closure.
