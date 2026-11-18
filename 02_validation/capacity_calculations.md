# Capacity Calculations

## Chart-reading rule

The app uses the conservative next-larger-radius rule. At a radius between table values, it uses the capacity from the next larger table radius. At an exact table radius, it uses that row's capacity.

## Required hand calculations

| Radius | Chart lookup | Allowed load | 90% warning | 100% tip threshold |
|---|---|---:|---:|---:|
| 62 ft | 75 ft row | 13,000 lb | 11,700 lb | 13,000 lb |
| 125 ft | Exact 125 ft row | 7,000 lb | 6,300 lb | 7,000 lb |
| 138 ft | 150 ft row | 5,500 lb | 4,950 lb | 5,500 lb |

Calculations:

1. `62 ft`: next larger table radius is 75 ft, so capacity is `13,000 lb`; `13,000 × 0.90 = 11,700 lb`.
2. `125 ft`: exact table radius, so capacity is `7,000 lb`; `7,000 × 0.90 = 6,300 lb`.
3. `138 ft`: next larger table radius is 150 ft, so capacity is `5,500 lb`; `5,500 × 0.90 = 4,950 lb`.

## Boundary tests

For each of the three calculations, the app should be tested at:

| Percentage | 62 ft expected | 125 ft expected | 138 ft expected |
|---|---|---|---|
| 89.9% | 11,687 lb: no warning | 6,293 lb: no warning | 4,945 lb: no warning |
| 90% | 11,700 lb: warning | 6,300 lb: warning | 4,950 lb: warning |
| 99.9% | 12,987 lb: no tip | 6,993 lb: no tip | 5,495 lb: no tip |
| 100% | 13,000 lb: tip | 7,000 lb: tip | 5,500 lb: tip |

## Staged-load checks

The available loads are 4,000 lb, 6,000 lb, 8,000 lb, and 10,000 lb.

| Load | At 50 ft | At 75 ft | At 100 ft | At 125 ft | At 150 ft |
|---|---|---|---|---|---|
| 4,000 lb | 20% safe | 31% safe | 44% safe | 57% safe | 73% safe |
| 6,000 lb | 30% safe | 46% safe | 67% safe | 86% safe | 109%: tip |
| 8,000 lb | 40% safe | 62% safe | 89% safe | 114%: tip | 145%: tip |
| 10,000 lb | 50% safe | 77% safe | 111%: tip | 143%: tip | 182%: tip |

The staged-load table confirms that all preset weights remain below capacity at some radii and cross warning/tip thresholds at others.
