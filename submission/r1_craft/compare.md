# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_152940.jpg
- L5+R1 mid ATTRIBUTE
- R6 mid MISSING
## adasind_167700.jpg
- L3 mid IGNORE_SCOPE
- L5+R4 center WRONG_CLASS
## adasind_212280.jpg
- L3+R3 edge ATTRIBUTE
- L1 mid SPURIOUS
- L5+R1 center DUPLICATE

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 10 | 9 | 1 | 2 |
| mid | 6 | 5 | 1 | 1 |
| edge | 2 | 2 | 0 | 0 |
