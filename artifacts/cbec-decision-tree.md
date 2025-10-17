# CBEC 경로(보세/직구) 의사결정 트리

```mermaid
flowchart TD
A[Start] --> B{ASP ≥ $60?}
B -- Yes --> C{체적중량 ≥ 1kg?}
B -- No  --> D{반품률 ≥ 15%?}
C -- Yes --> E[보세 +1]
C -- No  --> F[직구 +1]
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
K --> M{규제/인증 필요?}
L --> M
M -- Yes --> N[보세 +1]
M -- No  --> O[직구 +1]
N --> P{수요변동계수 ≤ 0.4?}
O --> P
P -- Yes --> Q[보세 +1]
P -- No  --> R[직구 +1]
Q --> S((추천: 보세备货))
R --> T((추천: 직구直邮))
