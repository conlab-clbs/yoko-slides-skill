# 図解アーカイブ｜やさしい学術教科書スライドの型ライブラリ

台本の各スライドは有限の「型」に分類できる。台本の `参照：P○（◯◯型）` や図解指示を下の型に割り当て、
**master_design_spec.md §4 の共通前文 ＋ 下の型別ブロック** でHiggsFieldプロンプトを組む。

英語は作画指示、日本語(タイトル/ラベル/キーメッセージ)はliteralで埋める。各型とも最後に
ピンク角丸ピルのキーメッセージを 72〜82% に置く。

> ★可読性（master §3.5）：**全ての文字を大きく**。語数を削る。**研究者名(A. Bandura等)の小添えは入れない**——
> 概念名（自己効力感・島皮質 等）を大きな主役ラベルにする。ラベルは各1〜数語。プロンプトには毎回
> 「ALL text very large/bold, few words, no small text/fine print」を含める（共通前文に内蔵済み）。

---

## A. 一言コンセプト中央型（宣言・キャッチ）
中央に特大コピー1行＋下に最小の象徴イラスト。余白多め。
```
This is a statement slide. Large bold rounded Japanese gothic main copy, centered, dark charcoal: 「{MAIN_COPY}」
Below it a minimal symbolic line-art motif: {MOTIF}. Lots of empty space.
Lower band (72–82%): rounded magenta-pink caption pill, bold white text: {KEY_MSG}
```
例) MAIN_COPY=自分にも"はい"と言える人になる / MOTIF=two small figures gently connected by one pink thread

## B. 上下2段対比型（Before / After）
上段＝旧状態(グレー寄り)、水平線、下段＝新状態(スカイブルー寄り＋小さな輝き)。
```
Two stacked rows compared. TOP row (muted gray, the old/negative state): {TOP}. A thin
horizontal divider. BOTTOM row (sky-blue, the new/positive state, a tiny sparkle): {BOTTOM}.
Title top: {TITLE}.  Lower band caption pill: {KEY_MSG}
```
例) TITLE=いい人モード vs 自分軸 / TOP=他人「はい」＋自分「本音は後回し」 / BOTTOM=他人「いいですよ」＋自分「私、これでいい」

## C. 左右2カラム対比型
中央に区切り。左右に対の線画＋短ラベル。差を面積/明暗で見せる。
```
Two side-by-side columns. LEFT: {LEFT}. RIGHT: {RIGHT}. A slim center divider. Title top: {TITLE}.
Small credit bottom-right if any: {CREDIT}. Lower band caption pill: {KEY_MSG}
```
例) 幸運派(明るいピンク電球) / 不運派(暗い電球)、強/近い・弱/遠い

## D. 横フロー3段階型（因果・手順の流れ）
左→右に3ノード、ピンク矢印で接続。各ノードに小さな線画アイコン＋短語。
```
A left-to-right flow with three stages joined by magenta-pink arrows, each a small clean
line-art icon with a short label: 1){S1}  2){S2}  3){S3}. Title top: {TITLE}.
Lower band caption pill: {KEY_MSG}
```
例) 相手の機嫌が悪そう → 扁桃体「危険！」 → いい人モード自動起動

## E. 横長ボックス型（学説・研究の図解）
中央に角丸の横長ボックス（極薄スカイブルー枠）。中に学説名＋因果を線画で。
```
A centered rounded horizontal box (very light sky-blue outline) presenting a theory:
heading {THEORY}, with a simple line-art cause-effect inside: {INSIDE}. A small relevant
line-art icon. Title top: {TITLE}. Lower band caption pill: {KEY_MSG}
```
例) THEORY=ジョン・ボウルビィ「愛着理論」 / INSIDE=いい子でいれば→安全→脳に「いい子戦略」が書き込まれる

## F. 3カード横並び型（3点まとめ・概要）
極薄スカイブルー枠の角丸カード3つ。各カードに線画アイコン＋番号＋短見出しのみ（本文なし）。
```
Three side-by-side rounded cards (very light sky-blue outlines), evenly spaced. Each card:
a small clean line-art icon + a number + a SHORT heading only (no body text):
card1 {C1ICON} ①{C1}; card2 {C2ICON} ②{C2}; card3 {C3ICON} ③{C3}. Title top: {TITLE}.
Lower band caption pill: {KEY_MSG}
```
例) ①心と身体が軽くなる ②人間関係が入れ替わる ③お金の流れが変わる

## G. 章番号付きステップ型（連番の各論）★番号は焼かない
左上を空けて生成→ `stamp --num 0X` で金番号を後合成。見出しが長い時は2行＋「左20%を空ける」指示。
```
Leave the TOP-LEFT corner completely empty (a number will be added later). Place the
heading horizontally centered (two centered lines if long): {HEADING}. Optional center
copy: {CENTER}. Diagram (center): {DIAGRAM}. Lower band caption pill: {KEY_MSG}
```
例) HEADING=情報のアンテナを立てる / DIAGRAM=漏斗(1,100万ビット→RAS→40ビット)

## H. タイトル/アジェンダ型（今日分かること）
ゴールド大見出し＋3項目の縦リスト（番号付き）。
```
Title band: {TITLE}. A large gold heading. Below, a vertical list of three numbered items,
large and clean: ①{I1} ②{I2} ③{I3}. Lower band caption pill (optional): {KEY_MSG}
```

## I. 特殊図解（必要時に作画を具体指定）
- **年表型**：横軸タイムライン＋等間隔ノード、各ノードに極小アイコン＋年＋一言、ピンク矢印で時間方向
- **漏斗型**：上＝大量の点＋数値、中央＝ラベル付き漏斗(くびれピンク)、下＝少数の点＋数値
- **氷山型**：水面上＝自覚(小)、水面下＝本当の原因(大)、薄青のスキャン線
- **脳＋拡大円型**：線画の脳＋拡大円で局所構造（島皮質/扁桃体/前頭前野などを位置で示す）
- **まとめグリッド型**：定義ピル1行＋下に2〜3カラム（各小アイコン＋ポイント）

---

## 割り当ての考え方
1. 台本の「②図解」記述を読み、上のA〜Iから最も近い型を選ぶ
2. 文字は「表示中に話している1フレーズ」だけに削る（master §3）
3. キーメッセージは1つ、ピンクピルに。重要語はピンクで強調可
4. 章番号があるスライド（変化1-3／習慣1-3 等）は型G扱い＝番号は焼かず後合成
5. 研究者名・学説名は図の小ラベルに留める（クライアントが消す場合あり → 局所消去で対応）
