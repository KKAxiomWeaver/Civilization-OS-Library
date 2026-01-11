

---

# K.K. Whitengineering • Multi-domain OS • Axiom Weaver

This repository contains all whitepapers authored by **K.K. (Axiom Weaver)**.
No folders used; papers organized via naming conventions + Master Index.

### Repository Structure Strategy

* All files stored at root (`/`)
* Naming:
  `2026-0111 - PainOS - RitualCultureOS - Works-on-My-Machine OS.md`

---

# Works-on-My-Machine OS

**「在我機器上很正常」文明系統：
責任轉移 × 環境差異 × 工程迷因 × 壓力逃脫 OS**
Version `0.1` — `2026-01-11`

**Author:** K.K. (Axiom Weaver)
**Affiliation:** *KKAxiomWeaver Whitepaper Research Center*
**License:** CC BY-NC-SA 4.0
© 2026 K.K.

---

## 📝 Abstract

**Works-on-My-Machine OS** 是從全球軟體工程、DevOps、SRE、QA、機房文化中萃取出的文明級語彙系統，用於描述一種最普遍、最典型的工程痛點現象：

> **「在我機器上跑得好好的。」
> “It works on my machine.”**

這句話是：

1. **責任轉移（Blame Shifting）**
2. **環境斷層（Environment Gap）**
3. **知識不完全（Partial State Awareness）**
4. **痛點幽默（Pain Humor）**
5. **迷因傳遞（Meme Propagation）**

本 OS 將它從一句抱怨轉成完整文明機制，
作為 PainOS 世界線的重要支柱之一。

---

## 01 — Problem Statement

### 1.1 為什麼全世界工程師都會說這句話？

因為軟體環境有以下巨坑：

* 本地環境 ≠ 伺服器環境
* Library 版本不一致
* Path 差異
* 設定不同
* Cache 污染
* 隱性依賴
* 資料狀態不同
* OS 不一致
* CPU/GPU/架構差異
* Locale 問題
* 時區問題
* 網路延遲

這些讓工程師面對同一句話的現實含義：

> **「我無法重現你的問題 → 不是我的錯。」**

這就是 Works-on-My-Machine 的核心邏輯。

---

## 02 — Concept Model

### 2.1 Works-on-My-Machine OS =

**環境差異 × 認知不對稱 × 責任逃脫 × 痛點幽默 × 迷因封裝**

五大核心模組：

1. **Env-Gap Module（環境差異模組）**

   * Dependency version gap
   * Config drift
   * Data state mismatch
   * Platform discrepancy

2. **Blame Deflection Process（責任偏移流程）**

   * “我的沒壞 → 應該是你那邊的問題。”
   * 典型職場生存技能。

3. **Pain Humor Layer（痛點幽默層）**

   * 讓工程師在崩潰中保持理智。

4. **State Ambiguity Engine（狀態模糊引擎）**

   * 工程師多半不知道對方的完整上下文。

5. **Memetic Transmission（迷因化傳播）**

   * 全球工程師自然使用此語，形成文化統一性。

---

## 03 — Mechanics（How It Works）

### 3.1 Works-on-My-Machine 流程（OS Flow）

```
[使用者或 QA 回報錯誤]
            ↓
[工程師重現 → 在本機沒問題]
            ↓
[說出 "works on my machine"]
            ↓
[責任瞬間轉移 / 壓力下降]
            ↓
[調查開始：環境差異？版本差？資料狀態？]
            ↓
[找到真因 or 強行 workaround]
            ↓
[事件被迷因化 / 成為 PainOS 資料庫]
```

### 3.2 語言為何可以降低痛感？

* 說出這句話 = 宣告「我先脫身」
* 形成心理緩衝 → 減少自責感
* 也等於「把問題送回給宇宙」
* 迷因化使工程師之間有共同語言
* 工作壓力瞬間下降

---

## 04 — Architecture

### 4.1 系統分層

* **Environment Layer（環境層）**
  設定、依賴、作業系統、硬體、資料。

* **Cognitive Layer（認知層）**
  工程師的有限上下文視角。

* **Linguistic Layer（語言層）**
  “Works on my machine.” 作為文明符號。

* **Pain Layer（痛點層）**
  用幽默處理不可預測的痛。

* **Culture Layer（文化層）**
  迷因傳播、部落格、論壇、Slack 上的痛點語言。

### 4.2 與 PainOS 的結構關係

Bug-as-Feature OS = 規格矛盾的語言解法
Works-on-My-Machine OS = 環境矛盾的語言解法

PainOS 世界線由這些子模組拼成整體文明。

---

## 05 — Use Cases

### 5.1 軟體工程

* 本地環境太乾淨 → 問題在別處
* 典型 debug 起點

### 5.2 DevOps

* 部署環境差異 → “不是程式的問題，是環境的問題。”

### 5.3 QA vs Dev 永恆戰爭

* QA：你壞掉了
* Dev：在我這邊很正常啊

### 5.4 機房 / SRE

* 設定差異造成 weird behavior
* 使用 Works-on-My-Machine 作為壓力緩衝語。

---

## 06 — Risks & Limitations

* 容易把真正環境問題推給他人
* 潛在 bug 可能因此延後被修
* 若文化氛圍過度依賴此語 → 會削弱團隊責任感
* 新人會誤以為不用記錄環境

---

## 07 — Comparative Analysis

| 語言系統                | 功能    | 主要用途          | 幽默密度  |
| ------------------- | ----- | ------------- | ----- |
| Bug-as-Feature      | 模糊規格  | 壓力轉換          | ⭐⭐⭐⭐⭐ |
| Works-on-My-Machine | 模糊責任  | 減少衝突          | ⭐⭐⭐⭐⭐ |
| Known Issue         | 歷史背鍋  | Documentation | ⭐⭐⭐   |
| By Design           | 跨部門緩衝 | 風險移轉          | ⭐⭐⭐⭐  |

Works-on-My-Machine = **責任轉移的文明語言最清晰的代表。**

---

## 08 — Implementation Path

### Stage I — Environment Mapping

列出影響問題重現的環境變數。

### Stage II — Pain Pattern Encoding

將常見 works-on-my-machine 案例擬合成 Pain Pattern。

### Stage III — Cultural Reinforcement

將痛點故事化、迷因化。

### Stage IV — Ops Integration

建立環境版本鎖定、config 管理流程（Infrastructure as Code）。

---

## 09 — Appendix

* 全球工程師最常見的 WMM（Works-on-My-Machine）案例
* 配置漂移（Config Drift）示意圖
* Dependency Hell vs Environment Hell 分析

---

## 10 — Glossary

* **WMM**：Works-on-My-Machine
* **Env Gap**：環境差異
* **Config Drift**：設定漂移
* **Pain Meme**：痛點迷因
* **Blame Deflection**：責任偏移

---

## 🔗 Related OS

* PainOS（主世界線）
* Bug-as-Feature OS
* Version Hell OS（下一篇）
* PagerDuty Nightmare Curve
* JinxOS

---

## 📚 How to Cite

K.K. (2026). *Works-on-My-Machine OS：環境差異文明系統*.
*KKAxiomWeaver Whitepaper Research Center.*
[https://github.com/KKAxiomWeaver/Whitepapers](https://github.com/KKAxiomWeaver/Whitepapers)

---
