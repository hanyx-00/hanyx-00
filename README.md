<div align="center">

# 朱 韓榮 ｜ JU HAN YOUNG

**バックエンドエンジニア志望**

*業務のルールを、正しく動くデータと計算に。*

<br>

![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![JPA](https://img.shields.io/badge/Spring_Data_JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
<br>
![JUnit5](https://img.shields.io/badge/JUnit_5-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

</div>

---

## 👋 About

大学で **物流学** を学び、在庫・発注・資材計画といった「業務のルール」に触れてきました。<br>
そのルールを、**データがずれず、計算が正しく、あとから根拠を説明できる** システムとして実装することに関心があり、バックエンドエンジニアを目指しています。

| | |
| --- | --- |
| 🎓 **学歴** | 慶星大学校（韓国・釜山）経済物流学部 物流学科 卒業（2025.02） |
| 💻 **研修** | Data Science Academy「Smart Cloud IT マスター AX/DX」日本 SW Developer 課程（2026.11 修了予定） |
| 🎯 **志望** | 日本の IT 企業でのバックエンド開発 |

---

## 🛠 Tech Stack

| 分野 | 技術 |
| --- | --- |
| Backend | `Java 17 / 21` `Spring Boot` `Spring Data JPA` `Spring Security` |
| Database | `PostgreSQL` `H2（テスト）` |
| Test / CI | `JUnit 5` `Mockito` `AssertJ` `GitHub Actions` |
| Frontend | `React` `Next.js` `TypeScript` `TanStack Query` `Tailwind CSS` |

---

## 📔 TADA ｜ AIダイアリーアプリ

> **チーム開発（5名）** · 2026.08 – 09 · 担当：人物キュレーター（API・画面）

日記を書くと、AIがステッカーを作ってカレンダーに残すサービスです。<br>
日記に出てくる人物を判定し、人ごとに日記をまとめる機能を担当しました。

```mermaid
flowchart LR
    AI["n8n + Gemini<br/>日記の解析"] -->|抽出結果| DS["DiaryService<br/>日記の保存"]
    FE["Next.js<br/>日記・人物の画面"] -->|REST| DS
    subgraph TX["同じトランザクション"]
        DS -->|イベント| CU["Curator<br/>検証・判定・集計"]
    end
    FE -->|REST| PA["Person API<br/>一覧・訂正"]
    CU --> DB[("PostgreSQL")]
    PA --> DB
    classDef mine fill:#EDF1FC,stroke:#2B50C8,color:#2B50C8,font-weight:bold
    classDef base fill:#F5F7FA,stroke:#8A93A3,color:#1A1F2B
    class CU,PA mine
    class FE,DS,AI,DB base
    style TX fill:#FAFBFE,stroke:#2B50C8,stroke-dasharray:4 3
```

<sub>🟦 青い部分が担当範囲</sub>

#### ✨ 取り組んだこと

| | 内容 |
| --- | --- |
| **人物判定** | 似た名前を誤ってまとめない4段階の判定（EXACT → SIMILAR → 履歴 → NEW） |
| **整合性** | 日記の保存と人物データを同じトランザクションで処理し、片方だけ残らないようにする |
| **同時保存** | 人物の行をロックしてから読み、上書きと主キーの衝突を防ぐ |
| **訂正・修正** | AIの候補と確定した人物を分離、本文修正は KEEP / ADD / REMOVE |
| **テスト** | 128件（人物判定 74件） |

📖 **詳しい説明** ▸ [**TADA README（日本語）**](https://github.com/hanyx-00/tada-was#readme)<br>
🔗 **Code** ▸ [Backend（Curator）](https://github.com/hanyx-00/tada-was/tree/main/src/main/java/com/tada/tada/curator) · [Frontend（Curator）](https://github.com/hanyx-00/tada-frontend/tree/main/domains/curator)　|　**Demo** ▸ [tada-frontend-seven.vercel.app](https://tada-frontend-seven.vercel.app)

---

## 📦 RESTOCK ｜ 在庫発注シミュレーター

> **個人開発** · 2026.09 · 担当：設計から画面・CIまですべて

需要の履歴から、在庫の発注量と発注日を計算するサービスです。<br>
物流学科で学んだ ABC分析・EOQ・安全在庫・MRP を、バックエンドから画面まで実装しました。

```mermaid
flowchart LR
    A["品目・需要の登録"] --> B["ABC分析<br/>3等級に分類"]
    B --> C["在庫方針<br/>EOQ・安全在庫・発注点"]
    C --> F["シナリオ比較<br/>費用の条件を変える"]
    A --> D["BOM・生産計画"]
    D --> E["MRP<br/>発注日を逆算"]
    classDef step fill:#F5F7FA,stroke:#8A93A3,color:#1A1F2B
    class A,B,C,D,E,F step
```

#### ✨ 取り組んだこと

| | 内容 |
| --- | --- |
| **安全在庫** | ABC等級に応じて基準（サービス水準）を変える |
| **MRP** | 部品構成と生産計画から、発注日を逆算する |
| **正確さ** | `BigDecimal` で計算、うるう年・需要0の日も考慮 |
| **検証** | 計算のテストと手計算で結果を照合、GitHub Actions で自動チェック |
| **構成** | Java 21 · Spring Boot 4.1 · PostgreSQL · React 19 |

📖 **詳しい説明** ▸ [**RESTOCK README**](https://github.com/hanyx-00/restock#readme)　|　🔗 **Code** ▸ [restock](https://github.com/hanyx-00/restock)

---

## 💡 開発で大切にしていること

1. **業務のルールを先に整理する** — 入力・単位・判断の条件を決めてから実装する
2. **データの整合性を守る** — 訂正や同時保存のあとも、数がずれない構造にする
3. **結果を確かめる** — テスト・手計算で、判断の根拠を残す

---

<div align="center">

📫 **Contact** ▸ a98220919@gmail.com

</div>
