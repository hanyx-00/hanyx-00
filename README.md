<div align="center">
朱 韓榮 ｜ JU HAN YOUNG

バックエンドエンジニア志望

業務のルールを、正しく動くデータと計算に。

Java · Spring Boot · Spring Data JPA · PostgreSQL · JUnit 5 · React · Next.js · TypeScript

</div>
📔 TADA ｜ AIダイアリーアプリ

チーム開発（5名）· 2026.08 – 09 · 担当：人物キュレーター（API・画面）　🟦 = 担当部分

日記を書くと、AIがステッカーを作ってカレンダーに残すサービスです。 日記に出てくる人物を判定し、人ごとに日記をまとめる機能を担当しました。

同じトランザクション
抽出結果
REST
イベント
REST
n8n + Gemini日記の解析
DiaryService日記の保存
Next.js日記・人物の画面
Curator検証・判定・集計
Person API一覧・訂正
PostgreSQL
取り組み	内容
人物判定	似た名前を誤ってまとめない4段階の判定（EXACT / SIMILAR / AMBIGUOUS / NEW）
同時保存	人物の行をロックしてから読む。2件同時保存の実験で400回とも正確
訂正と修正	AIの候補と確定した人物を分離。本文修正は KEEP / ADD / REMOVE で反映
テスト	124件（人物判定 74件）

🔗 Backend（tada-was） · Frontend（tada-frontend） · Demo

📦 RESTOCK ｜ 在庫発注シミュレーター

個人開発 · 2026.09 · 担当：設計から画面まですべて

需要の履歴から、在庫の発注量と発注日を計算するサービスです。 ABC分析・EOQ・安全在庫・MRPを、バックエンドから画面まで実装しました。

品目・需要の登録
ABC分析3等級に分類
在庫方針EOQ・安全在庫・発注点
シナリオ比較費用の条件を変える
BOM・生産計画
MRP発注日を逆算
構成	
Backend	Java 21 · Spring Boot 4.1 · Spring Data JPA · PostgreSQL
Frontend	React 19 · TypeScript · Vite
Test	JUnit 5 · Mockito · AssertJ（計算のテスト7件）

🔗 Repository（restock）

💡 開発で大切にしていること
業務のルールを先に整理する — 入力・単位・判断の条件を決めてから実装する
データの整合性を守る — 訂正や同時保存のあとも、数がずれない構造にする
結果を確かめる — テスト・実験・手計算で、判断の根拠を残す
<div align="center">

📫 a98220919@gmail.com

</div>
