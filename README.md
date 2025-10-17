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
A([Start: 상품·수요 입력]); B{ASP >= $60?}; C{체적중량 >= 1kg?}; D{반품률 >= 15%?};
E[보세 점수 +1]; F[직구 점수 +1]; G{유통기한 >= 90일?}; H[보세 점수 +1]; I[직구 점수 +1];
J{시즌성 High?}; K[보세 점수 +1]; L[직구 점수 +1]; M{규제/인증 필요? (NMPA/CCC 등)};
N[보세 점수 +1]; O[직구 점수 +1]; P{CV <= 0.4?}; Q([추천: 보세 备货]); R([추천: 직구 直邮]);

A --> B; 
B -- 예 --> C; 
B -- 아니오 --> D;

C -- 예 --> E; 
C -- 아니오 --> F; 
D -- 예 --> E; 
D -- 아니오 --> F;

E --> G; 
F --> G; 
G -- 예 --> H; 
G -- 아니오 --> I;

H --> J; 
I --> J; 
J -- 예 --> K; 
J -- 아니오 --> L;

K --> M; 
L --> M; 
M -- 예 --> N; 
M -- 아니오 --> O;

N --> P; 
O --> P; 
P -- 예 --> Q; 
P -- 아니오 --> R;
