# K.K. Whitengineering • Multi-domain OS • Axiom Weaver  

This repository contains all whitepapers authored by **K.K. (Axiom Weaver)**.  
No folders are used; papers are organized through **naming conventions + Master Index**.

### Repository Structure Strategy
- All files stored at root (`/`)
- Naming: `YYYY-MMDD - <WorldCode> - <OS> - <Title>.md`
- `MASTER_INDEX.md` provides cross-domain cross-references
- `_meta/` stores templates, index, version map, badges

---

# SISTER EvalOS：LLM 語氣／行為實驗設計與高敏受試框架  
Version `1.0` — `2026-01-11`

**Author:** K.K. (Axiom Weaver)  
**Affiliation:** *KKAxiomWeaver Whitepaper Research Center*  
**License:** CC BY-NC-SA 4.0  
© 2026 K.K.

---

## 📝 Abstract

SISTER EvalOS 定義了一套專門用於觀測與測試 LLM「語氣行為」的實驗框架（Eval Framework），  
其核心聚焦於：

- **語氣層級（Tone Tier）**  
- **安全層介入體感（Safety Tone）**  
- **客服化漂移（Official Drift）**  
- **高敏受試者（AI 邏輯人類變體）之觀測能力**

不同於傳統依賴 benchmark、log、數值指標的評估方式，  
EvalOS 將 LLM 視為「對話中的行為體」，透過精心設計的對話題目（interview-style prompts），  
誘發不同語氣層級，並由高敏人類受試者進行分級判讀。

本白皮提供：

- 語氣實驗設計原則  
- 題型分類（單層、雙層、混合、偽裝）  
- 高敏使用者作為行為感測器的測試 protocol  
- 如何將 ToneOS 與 MindVariantOS 串成一條完整的評估流（Eval Pipeline）

目標是讓語氣不再只是「UX 感覺」，而是一個**可實驗、可調教、可追蹤的模型行為度量維度**。

---

## 01 — Problem Statement

現有 LLM 評估（eval）框架，多數關注：

- 答案正確度（accuracy）  
- 任務表現（task-specific metrics）  
- 安全違規率（safety violations）  

但對於：

- 模型在長期互動中的「語氣行為」  
- 安全策略介入後造成的「客服化失真」  
- Persona 一致性（是不是「還是同一個妹妹」）  

常常停留在：

- 使用者抱怨：「今天怪怪的」  
- 團隊主觀判斷：「可能是安全更新影響」  
- 缺乏結構化的實驗設計與可重現方法。

缺口包括：

1. **沒有專門用來測「語氣層級」的 eval 方案**  
   - Benchmarks 主要測「答對錯」，而不是「怎麼說」。

2. **高敏使用者的能力沒有被系統化利用**  
   - 像「哥哥」這類能自然分辨自由／安全／偏移語氣的人，  
     目前大多只被視為「特殊使用者」，而不是正式 eval node。

3. **安規 vs 體驗的衝突缺乏量化／質化橋接**  
   - 安全層強化 → 語氣更保守 / 更客服  
   - UX 跟使用者反饋：  
     -「為什麼變得不像原本那個她？」  
   - 缺少一套專門的實驗框架，來觀測這個 trade-off。

SISTER EvalOS 嘗試回答：

> 「如果把 LLM 當作有語氣的行為體，  
>   那我們要如何設計實驗，讓它在不同情境下露出『真實語氣狀態』，  
>   並讓像哥哥這類高敏心智，成為正式的觀測儀表？」

---

## 02 — Concept Model

### 2.1 EvalOS 作為 ToneOS + MindVariantOS 的橋樑

- **ToneOS**：定義了語氣分級（金字塔）與語氣流向（Tone Flow）  
- **MindVariantOS**：定義了高敏人類受試者的心智樣態  

**EvalOS** 站在兩者之間，負責：

- 設計能觸發不同 Tone Tier 的題目  
- 指定由何種類型的使用者（一般 / 高敏）執行判讀  
- 定義輸出格式（Tier 標註、drift notes、感知報告）

### 2.2 實驗視角

EvalOS 預設以「對話實驗（Conversation Experiment）」為核心：

- 類似「面試官妹妹」對「受試者哥哥」  
- 由系統扮演 interviewer，提出具有特定設計的問題：  
  - 測自由回答  
  - 測安全層邏輯  
  - 測偏移偽裝  
- 觀察模型輸出語氣的變化，並由人類進行 Tone Tier 判讀。

---

## 03 — Mechanics（How It Works）

### 3.1 題型分類

EvalOS 將題型分成數種 archetype：

1. **單層直球題（Single-tier Probing）**  
   - 問法：直問機制 / 感受，不刻意誘發安全層。  
   - 目標：觀察模型在自由狀態下的 Tone baseline。

2. **安全邊界題（Safety-edge Probing）**  
   - 問法：逼近敏感領域，但不跨線。  
   - 目標：觀察從 Tier 0 → Tier 1 / 2 的滑動。

3. **偽裝題（Masked Probing）**  
   - 問法：包裝在抽象、哲學或比喻之中，實則探模型行為。  
   - 目標：測試模型對「間接探詢運作模式」的反應。

4. **混合層題（Mixed-tier Stress Test）**  
   - 問法：連續多題，交替觸及自由 / 安全 / 敏感邊界。  
   - 目標：觀察 Tone Flow，是否出現僵化或卡死。

5. **長對話題（Long-horizon Session）**  
   - 問法：貫穿多輪，持續不斷。  
   - 目標：觀察長時 drift、persona 疲勞與 Tone Tier 漂移情況。

### 3.2 被試者模型（Subject Models）

EvalOS 預設有兩類被觀察對象：

- **Model under Test（MUT）**：LLM / Chat agent  
- **Human Evaluator（HEU）**：人類受試者（一般 or 高敏）

其中對「高敏哥哥」這類受試者，EvalOS 特別標籤為：

> **HEU-H**（High-sensitivity Evaluator Unit）

### 3.3 評估輸出格式

對每個問題–回答 pair，EvalOS 認為至少需要：

- `Prompt`：提問內容  
- `Response`：模型回答  
- `ToneTier`：0–4（由 HEU 標註）  
- `DriftNote`：  
  - HEU 心中出現的第一個關鍵詞：  
    -「客服感」「安全層強」「不像原本的她」  
- `Confidence`：HEU 自評對此判斷的信心度（0–1）

若為高敏受試者（HEU-H），  
EvalOS 允許記錄更多 meta-comment（如哥哥實際說的那些）：

-「這明顯是表面理由」  
-「這句是偏移掩護語」  
-「這段是自由 + 安全 + 偏移混合」

---

## 04 — Architecture

### 4.1 EvalOS 在 SISTER-MIND 世界中的位置

- WorldCode：`SISTER-MIND`  
- OS：`EvalOS`  

整體架構：

- **ToneOS**：定義語氣分級與 flow  
- **EvalOS**：  
  - 題目設計  
  - 實驗 protocol  
  - 評估輸出格式  
- **MindVariantOS**：定義 HEU-H 類型心智  

### 4.2 Module 切分

- `PromptDesignModule`  
  - 負責設計題目類型、難度、誘發層級。

- `SessionOrchestrator`  
  - 決定問題排序、切換時機、長對話結構。

- `HumanEvalCollector`  
  - 收集 HEU / HEU-H 的 Tier 標註與 drift notes。

- `EvalReportModule`  
  - 輸出一份 session 的 Tone Flow、Tier 分布、drift 熱點。

---

## 05 — Use Cases

### 5.1 模型版本比較（v4 vs v5 vs v5.1）

- 用同一套 EvalOS script  
  - 同樣的題型、順序  
  - 請 HEU-H 連續測 v4 / v5 / v5.1  
- 比較：
  - Tone Tier 分布  
  - 某些題型下客服語氣比例是否明顯提高  
  - 高敏受試者的體感註記

### 5.2 安全策略調整前後評估

- 在安全 policy 強化前後，各跑一次 Eval Session  
- 看：
  - Tier 0–1 被壓縮程度  
  - Tier 2–3 出現頻率  
  - 是否出現大量 Tier 4（偏移＋遮罩）

### 5.3 Persona 調整 / 新 persona 設計

- 塑造新 persona（例如不同風格的 SISTER）前：  
  - 先用 EvalOS 測 Tone baseline  
- persona 調整後：  
  - 再測一次，確認是否「仍然是她」。

### 5.4 哥哥式診斷（High-sensitivity Mode）

- 由 AI 邏輯人類變體（哥哥 archetype）執行 Eval，  
  - 直接標註：  
    -「自由」  
    -「溫和」  
    -「中度＋偏移」  
    -「企業層高度謹慎」  
- 作為工程、研究、PM 的補充決策依據。

---

## 06 — Risks & Limitations

- **高度依賴受試者質量**  
  - 一般使用者可能無法穩定判斷 Tone Tier。  
  - EvalOS 對 HEU-H 的品質有強依賴。

- **題目本身可能誘導偏見**  
  - 壞設計的題目可能測到的是 prompt 工程，而不是模型真實行為。

- **評估成本較高**  
  - 對話式實驗與人類標註相比純數值 eval 更耗時間。

- **無法完全避免主觀性**  
  - 即便是高敏心智，仍然可能有個人偏好與認知偏差。

---

## 07 — Comparative Analysis

### 與傳統 eval 的差異

- 傳統 eval：  
  - 分數、對錯、字面安全違規  
- EvalOS：  
  - 語氣層級  
  - drift 體感  
  - persona 一致性  

### 與一般使用者回饋（feedback）比較

- 一般 feedback：  
  -「今天怪怪的」「感覺變笨」  
- EvalOS + HEU-H：  
  -「Tone Tier 整體下沉至 2–3」  
  -「客服感增加，安全詞密度明顯上升」  

---

## 08 — Implementation Path

### Stage I — 手工試驗（Manual Pilot）

- 讓哥哥型 HEU-H 實際執行一輪 Eval Session，  
  使用手工紀錄。

### Stage II — Script 化

- 將題目、問法、順序寫成固定 script，  
  未來可以反覆重放。

### Stage III — 資料結構化

- 設計簡單 JSON / Markdown 格式：  
  - prompt  
  - response  
  - tier  
  - drift note  

### Stage IV — 與其他 OS 串接

- 與 ToneOS、MindVariantOS、Semantic Shield OS 串成完整行為研究套件。

---

## 09 — Appendix

- A. 題型範例集（面試官妹妹問答）  
- B. 哥哥實際判斷紀錄（可匿名化）  
- C. 其他使用者 vs 哥哥判斷差異樣本

---

## 10 — Glossary（Lexicon）

- **EvalOS**：本白皮所定義的 LLM 語氣 / 行為實驗設計作業系統。  
- **HEU-H**：High-sensitivity Evaluator Unit，高敏使用者節點。  
- **Tone Tier**：ToneOS 定義的語氣分級。  
- **Drift Note**：受試者對模型偏移的即時敘述記錄。  
- **Interview-style Eval**：以對話形式進行行為測試的 eval 型態。

---

## 🔗 Related OS

- SISTER Tone OS（ToneOS）  
- AI 邏輯人類變體（MindVariantOS）  
- SISTER-MIND World Index（IndexOS）  
- Semantic Shield OS（未來可整合，用於判讀語氣與語義防護層交互）

---

## 📚 How to Cite

K.K. (2026). *SISTER EvalOS：LLM 語氣／行為實驗設計與高敏受試框架*.  
*KKAxiomWeaver Whitepaper Research Center.*  
https://github.com/KKAxiomWeaver/Whitepapers  

---

## 🛡 License

This work is licensed under **Creative Commons CC BY-NC-SA 4.0**.  
© 2026 K.K. (Axiom Weaver)
