<h1 align="center">🇨🇳 China Value Chain Toolkit</h1>
<p align="center">
CBEC 경로 의사결정 · Vendor/QA/OTD 로드맵 · 중국 라벨/표준(GB/CCC) 체크리스트
<br>
<sub>Retail · Consumer · Light Manufacturing · KOR/CHN/ENG</sub>
</p>

<p align="center">
  <img alt="license" src="https://img.shields.io/badge/License-MIT-black?style=flat-square">
  <img alt="format" src="https://img.shields.io/badge/Format-Markdown%20%7C%20CSV-blue?style=flat-square">
  <img alt="mermaid" src="https://img.shields.io/badge/Diagram-Mermaid-00AA88?style=flat-square">
  <img alt="prs" src="https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square">
</p>

---

## 📌 Overview
중국향 커머스/제조 실무에서 **결정·설계·준수** 아티팩트 모음.

- **CBEC Decision Tree**: 보세备货(BBC) vs 직구直邮(BC Direct) — *경로선택·리스크·비용 비교*
- **Vendor–QA–OTD Roadmap**: 리드타임 분해·병목·개선 레버·SLA 예시 — *납기/불량/벌과금 설계*
- **GB/CCC Checklist**: 카테고리별 필수 라벨·서류 — *통관·표준 준수*

---

## 🗂 Artifacts
| Artifact | Link | Format | Best for |
|---|---|---|---|
| **CBEC Decision Tree (보세/직구)** | [`artifacts/cbec-decision-tree.md`](artifacts/cbec-decision-tree.md) | Markdown + Mermaid | 경로선택, 비용/리스크 비교 |
| **Vendor–QA–OTD Roadmap** | [`artifacts/vendor-otd-roadmap.md`](artifacts/vendor-otd-roadmap.md) | Markdown + Mermaid | 납기/불량/벌과금 설계 |
| **GB/CCC Checklist** | [`MD`](artifacts/gb-ccc-checklist.md) · [`CSV`](artifacts/gb-ccc-checklist.csv) | MD · CSV | 통관·라벨 사전 점검 |

---

## 🧭 60-Second Use
1. **경로선택** — `CBEC Decision Tree`의 질문(ASP·체적중량·반품률·유통기한·시즌성·규제·CV)을 순차로 답하면 **BBC/직구**가 도출.  
2. **납기·품질 설계** — `Vendor–QA–OTD`에서 리드타임을 단계별로 분해하고 **PPK/PSI·대체벤더·QC 샘플링·SLA** 레버를 선택.  
3. **준수 점검** — `GB/CCC Checklist`에서 카테고리별 **표준/라벨/서류**를 확인.

> 실제 의사결정은 세금·물류단가·SLA/CS까지 함께 비교하는 것을 전제로.

---

## 🔍 Preview (Mermaid)

```mermaid
flowchart LR
A([Start: Input product and demand]); 
B{ASP >= 60 USD}; 
C{Volumetric weight >= 1 kg}; 
D{Return rate >= 15 pct}; 
E[Bonded score +1]; 
F[Direct score +1]; 
G{Shelf life >= 90 days}; 
H[Bonded score +1]; 
I[Direct score +1]; 
J{Seasonality high}; 
K[Bonded score +1]; 
L[Direct score +1]; 
M{Regulatory or certification needed}; 
N[Bonded score +1]; 
O[Direct score +1]; 
P{Demand CV <= 0.4}; 
Q([Recommend Bonded]); 
R([Recommend Direct]);

A --> B; 
B -- yes --> C; 
B -- no  --> D;

C -- yes --> E; 
C -- no  --> F; 
D -- yes --> E; 
D -- no  --> F;

E --> G; 
F --> G; 
G -- yes --> H; 
G -- no  --> I;

H --> J; 
I --> J; 
J -- yes --> K; 
J -- no  --> L;

K --> M; 
L --> M; 
M -- yes --> N; 
M -- no  --> O;

N --> P; 
O --> P; 
P -- yes --> Q; 
P -- no  --> R;

P -- yes --> Q
P -- no  --> R
