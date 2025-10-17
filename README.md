<h1 align="center">🇨🇳 China Value Chain Toolkit</h1>
<p align="center">
CBEC 경로 의사결정 · Vendor/QA/OTD 로드맵 · 중국 라벨/표준(GB/CCC) 체크리스트  
<br>
<sub>Trilingual candidate (KOR / CHN / ENG) — Retail · Consumer · Light Manufacturing focus.</sub>
</p>

<p align="center">
  <a href="https://github.com/JUNHOJO-korea/china-value-chain-toolkit/stargazers">
    <img alt="stars" src="https://img.shields.io/github/stars/JUNHOJO-korea/china-value-chain-toolkit?style=flat-square">
  </a>
  <a href="https://github.com/JUNHOJO-korea/china-value-chain-toolkit/commits/main">
    <img alt="last commit" src="https://img.shields.io/github/last-commit/JUNHOJO-korea/china-value-chain-toolkit?style=flat-square">
  </a>
  <a href="#license">
    <img alt="license" src="https://img.shields.io/badge/License-MIT-black?style=flat-square">
  </a>
  <img alt="made with" src="https://img.shields.io/badge/format-Markdown%20%7C%20CSV-blue?style=flat-square">
  <img alt="PRs" src="https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square">
</p>

---

## 👀 What is this?
중국향 커머스/제조 실무에서 바로 써먹는 **1-페이지 아티팩트** 모음입니다.  
채용/프로젝트 상황에서 “바로 설명·결정·실행”을 돕도록 설계했어요.

- **CBEC 경로 의사결정 트리** — 보세备货(BBC) vs 직구直邮(BC Direct) 선택  
- **Vendor–QA–OTD 로드맵** — 리드타임 분해, 병목·개선 레버, 기대효과 매핑  
- **중국 라벨/표준(GB/CCC) 체크리스트** — 카테고리별 필수 표기 & 서류

> 목적: 리드타임/전환율/OTD/반품률/규제리스크를 **짧은 문서**로 관리

---

## 🗂 Artifacts
| Artifact | Link | Format | Best for |
|---|---|---|---|
| CBEC Decision Tree (보세/직구) | [`artifacts/cbec-decision-tree.md`](artifacts/cbec-decision-tree.md) | Markdown + Mermaid | 경로선택·비용/리스크 비교 |
| Vendor–QA–OTD Roadmap | [`artifacts/vendor-otd-roadmap.md`](artifacts/vendor-otd-roadmap.md) | Markdown + Mermaid | 납기/불량/벌과금 설계 |
| GB/CCC Checklist | [`artifacts/gb-ccc-checklist.md`](artifacts/gb-ccc-checklist.md) · [`CSV`](artifacts/gb-ccc-checklist.csv) | MD · CSV | 통관·라벨 사전 점검 |

---

## 🔎 Preview (Mermaid)
아래는 저장소 내 Mermaid를 이용한 **요약 미리보기**입니다.

```mermaid
flowchart LR
A[CBEC 경로선택] --> B{ASP / 체적중량 / 반품률}
B -->|고가·고체적| C[보세 유리 +]
B -->|저가·경량| D[직구 유리 +]
C --> E{유통기한·시즌성·규제}
D --> E
E -->|규제·시즌성 높음| F((보세 备货))
E -->|규제 없음·짧은 유통기한| G((직구 直邮))
