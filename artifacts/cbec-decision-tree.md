# CBEC 경로(보세备货 vs 직구直邮) 의사결정 트리

중국향 판매 시 상품 특성과 리스크를 기준으로 **보세备货(BBC)** 또는 **직구直邮(BC Direct)** 를 빠르게 선택하는 1-page 가이드.

---

## 0) 입력 파라미터(필수)
| Key | 설명 | 권장 소스 |
|---|---|---|
| `ASP` | 평균 판매가(USD) | 내부 매출/경쟁사 벤치 |
| `Volumetric` | 체적중량(kg) = (L×W×H cm)/6000 | 포장 스펙 |
| `ReturnRate` | 반품률(%) | 카테고리/채널 히스토리 |
| `ShelfLife` | 유통기한(일) 또는 패션 시즌성 | 성분·라벨/MD |
| `Seasonality` | High / Low | 판매 히트맵 |
| `Regulated` | 특수화장품·식품·전기안전 등 규제 필요(Y/N) | NMPA/CIQ/CCC |
| `CV` | 수요변동계수 = σ/μ | 예측·실적 |

---

## 1) 결정 트리 (Mermaid)
```mermaid
flowchart TD
  A[Start: 상품 특성 입력] --> B{ASP ≥ $60?}
  B -- Yes --> C{체적중량 ≥ 1kg?}
  B -- No --> D{반품률 ≥ 15%?}
  C -- Yes --> E[보세 유리 +1]
  C -- No  --> F[직구 유리 +1]
  D -- Yes --> E
  D -- No  --> F
  E --> G{유통기한 ≥ 90일?}
  F --> G
  G -- Yes --> H[보세 +1]
  G -- No  --> I[직구 +1]
  H --> J{시즌성 High?}
  I --> J
  J -- Yes --> K[보세 +1]
  J -- No  --> L[직구 +1]
  K --> M{규제/인증 필요? (NMPA/식품/CCC)}
  L --> M
  M -- Yes --> N[보세 +1]
  M -- No  --> O[직구 +1]
  N --> P{수요변동계수(CV) ≤ 0.4?}
  O --> P
  P -- Yes --> Q[보세 +1]
  P -- No  --> R[직구 +1]
  Q --> S((추천: 보세备货))
  R --> T((추천: 직구直邮))
