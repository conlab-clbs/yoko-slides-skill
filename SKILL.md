---
name: yoko-slides
description: 葉子/Y-シリーズ動画台本の「スライド設計リスト」から、梅﨑さん好評の「やさしい学術教科書」線画イラストのスライドをHiggsField(nano_banana_pro)で一気通貫制作するスキル。台本番号を渡すと、台本解析→図解の型割当→プロンプト生成→画像生成→白箱除去→テロップ余白確保→金番号合成→16:9フルブリードPPTXまで自動で行う。水彩タッチ/暗いCGは禁止しクリーン線画で統一する。「yoko-slides」「葉子のスライド」「Y-008のスライド作って」「教科書的な図解スライド」「願望実現スライド」「台本のスライドを作って(葉子)」などで使用。クリーン線画の統一デザイン規格・後処理パイプライン込み。台本そのものの執筆や、暗いネイビーCG系(量子脳コーチ3Days)は対象外。
---

# yoko-slides

葉子チャンネル（Y-シリーズ／心理学×AI波動「ロジカル願望実現メソッド」）の動画台本に付いている
**「スライド設計リスト」**を、**やさしい学術教科書スタイルのクリーン線画スライド**へ落とし込み、
HiggsField で生成して PPTX まで仕上げる。Y-007 で梅﨑さん好評の基準を仕組み化したもの。

## 最初に必ず読む（正典）
- `reference/master_design_spec.md` … 共通デザイン規格（**水彩禁止**・パレット・4ゾーン・共通プロンプト前文・ハマりどころ）
- `reference/diagram_archetypes.md` … 図解の型ライブラリ（A〜I）＋型別プロンプト
- 後処理ツール … `scripts/slide_tools.py`（whitefix / stamp / telopsafe / pptx / audit）

> 台本側の「デザイン仕様」に水彩等が残っていても**無視**し、本スキルの規格を適用する。

## 入力
- 台本番号（例 `008`）。台本ファイルは `~/Downloads/*Y0?08*` や `*008*` を検索、無ければユーザーに場所を確認。
- 台本末尾に「NotebookLM入力用：スライド設計リスト（全N枚）」がある前提。

## ワークフロー

### STEP 0｜準備
1. 台本ファイルを特定し全文読む（特に「スライド設計リスト」と本文のタグ `[スライドN]` 位置）。
2. 出力先 `projects/Y-0XX_<topic>/`（`slides/_raw`, `slides/telop_safe`, `refs/`）を作成し、台本を `refs/` にコピー。
3. HiggsField の残高/疎通を確認（`balance`）。

### STEP 1｜設計（型割当表を作る）★人手レビュー推奨
スライド設計リストの各スライドを読み、`diagram_archetypes.md` のA〜Iに割り当て、
`projects/Y-0XX_<topic>/スライド作成指示書.md` に表で書き出す（番号スライドは型G＝番号は焼かない）。
各行：スライド番号 / 役割 / 採用する型 / 図解の作画内容 / タイトル / キーメッセージ / 章番号(あれば)。

### STEP 2｜プロンプト生成＆画像生成
- 各スライド = `master §4 共通前文` ＋ `型別ブロック`。日本語はliteralで。
- `generate_image` model=`nano_banana_pro`, aspect_ratio `16:9` で生成（章番号スライドは**番号を入れず左上を空ける**）。
- 8枚程度ずつバッチ投入→`job_display`でURL取得→`slides/_raw/slideNN_<topic>.png` にDL。
- **全枚を目視**し、漢字崩れ・図解破綻のあるものだけ再生成（プロンプトに "PERFECT accurate kanji"）。

### STEP 3｜後処理（機械処理で品質担保）
```bash
S=~/.claude/skills/yoko-slides/scripts/slide_tools.py
P="/path/to/projects/Y-0XX_<topic>"
# 1) 章番号スライドだけ、番号を統一デザインで合成（生成時は番号なし）
python3 "$S" stamp "$P/slides/_raw/slide06_xxx.png" "$P/slides/_raw/slide06_xxx.png" --num 01
#   …該当スライド分くり返し（01,02,03）
# 2) 白箱除去 → テロップ余白 → PPTX を一括
python3 "$S" finish "$P/slides/_raw" "$P/slides/telop_safe" "$P/Y-0XX_<topic>_スライドNN枚.pptx"
# 3) 余白チェック
python3 "$S" audit "$P/slides/telop_safe"
```
- 番号合成は `finish` の前に原本(`_raw`)へ行うこと（telop_safeは原本を縮小するため）。
- `audit` で「余白不足」が出たスライドは個別に対処（通常はtelopsafe済みなら0枚）。

### STEP 4｜納品＆確認
- PPTX とサムネ数枚をユーザーに提示。気になる差し替え・文言調整に対応。
- 研究者名など**クライアントが消したい文字**は再生成より局所PIL消去が確実（master §6）。

## やってはいけない
- 水彩タッチ／可愛い系、暗いネイビーCG＋金枠グロー、写真・3D合成
- 章番号を画像に焼き込む（字形がばらつく → 必ず `stamp`）
- 下部15%にコンテンツを残す（必ず `telopsafe`）
- ピンクの多用（差し色は1点に集中）
- **小さな文字・fine print**（研究者名の小添え、長い箇条書き、ちまちました注釈）。スマホ縦・最小表示で中高年女性が読めないサイズは不可（master §3.5）。語数を削って全文字を大きく。コンタクトシート(幅480px)で読めるか必ず検証し、読めなければ作り直す。

## メモ
- 関連メモリ: `feedback_yoko_slide_lineart_style`（正解の見本＝セリグマン犬）
- 暗いネイビーCG方式は別物 → `reference_higgsfield_seminar_slides`（量子脳コーチ3Days）
