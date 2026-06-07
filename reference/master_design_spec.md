# マスターデザイン規格｜やさしい学術教科書スライド（葉子/Y-シリーズ共通）

> 全案件共通の唯一の正典。各台本の「デザイン仕様」節に水彩等の記載が残っていても、**本規格が優先**する。
> 梅﨑さん確認済み・好評の Y-007 で確立した基準。

---

## 0. 画風の正解（最重要）

**「学術専門書の図版を、女性向けにやさしく描き直したクリーンな線画イラスト」**。
大学講義のような硬さはなく、知的で端正。

- ✅ 正解の見本（OK確定）：`【AIA】梅﨑さん/.../ep6_media_final/slides/slide_05_セリグマン犬の実験.png`（最優先）、`slide_08_アンカリング効果.png`、`slide_09_RAS網様体賦活系.png`、章扉は `slide_04_章扉_学習性無力感.png`
- 🚫 **水彩タッチは禁止**（梅﨑さんフィードバック）。にじみ・ぼかし・絵の具感・可愛い系NG
- 🚫 暗いネイビー宇宙地＋金枠＋グロー発光の重厚CG（3Daysスライド系）も**禁止**
- 🚫 写真・3D・実写合成も不可。あくまで線画イラスト
- 🚫 **可愛くしすぎない（大人トーン）**：キラキラ/星/ハート/魔法のステッキ/お姫様風ドレスの女性などのファンシー要素は禁止。人物は**素朴で自然な線画**（普段着・自然な姿勢）。大人が真剣に見る動画に合う、端正で落ち着いた教科書図版にする。色味（クリーム＋インディゴ＋スカイブルー＋ピンク差し色）は親しみやすく保ってよいが、モチーフを子供っぽくしない。

> 旧台本に残る「イラスト：水彩タッチ」「キャプション水色背景」等は**無視して本規格に置換**する。

---

## 1. カラーパレット

| 要素 | 指定 |
|---|---|
| 背景 | 明るい温かみのあるオフホワイト #F5F0E8（〜#F7F5F1）。**上下端まで完全フラットな単色**。白帯・グラデ・色分け禁止 |
| 主線 | ダークインディゴ #2E3A59（細い均一ライン） |
| サブ面・補助線 | やわらかいスカイブルー #C5E0F0（淡く控えめに） |
| アクセント差し色 | マゼンタピンク #FF4D88（〜#E84A8A）。**キーワード・キーメッセージ枠だけ**に使用 |
| ゴールド | #C9A14A。**章番号（01/02/03）のみ**。本文図解では使わない |
| 文字 | チャコール #333333、太字の丸ゴシック（Noto Sans JP Bold 想定） |

---

## 2. レイアウト4ゾーン（テロップ対応・厳守）

```
0%   ┌──────────────────────────┐
     │ タイトル（章番号＋見出し）       │ 0〜18%
18%  ├──────────────────────────┤
     │ メイン図解ゾーン（主役）         │ 18〜70%
70%  ├──────────────────────────┤
     │ キーメッセージ（ピンク角丸ピル）   │ 70〜82%
82%  ├──────────────────────────┤
85%  │ ░ テロップ専用・完全空白 ░     │ 85〜100%
100% └──────────────────────────┘
```

- 下部15%（85〜100%）は**図・文字・線を一切置かない**。ただし**背景色は上部と同一**のまま（白帯・色分けを作らない）
- キーメッセージ／キャプションの下端は**82%以内**
- 出典クレジット（例 `Seligman, 1967`）は図の隅に**小さく・薄いブルー**で
- ※生成時に下部余白が守られないことが多い → 後処理 `telopsafe` で機械的に必ず確保する（§5）

---

## 3. 文字3原則

1. スライドに載せるのは「そのスライド表示中に話している1フレーズ」だけ
2. 話していない補足文・説明文は載せない（図のラベルは最小の単語のみ）
3. タイトル以外の文字は**極力減らし、大きく**。箇条書きは最大3点・各1行

## 3.5 可読性ルール ★最重要（スマホ縦・最小表示・中高年女性が読める）

> 視聴者の多くは**スマホ縦画面**で見る。16:9が縦画面の小さな枠に収まった状態で、**中高年女性がはっきり読める**ことを絶対基準にする。図中の小ラベル（例「自己効力感」）が読めないのは不可。

- **語数を削るのが最大の手段**：文字を大きくする＝言葉を減らす。1スライドの文字要素は「大タイトル1／大ラベル最大3／ピンクのキーメッセージ1」程度に圧縮する。
- **最小文字サイズの目安**：どんなラベルも**画面高さの約5%以上**（タイトル≈7〜9%、中央コピー≈7%、キーメッセージ≈5〜6%）。これ未満の文字は作らない。
- **表題は大きく、ただしバランス**：タイトルだけ巨大にして他とアンバランスにしない（巨大化禁止）。
- **fine print 禁止**：研究者名（A. Bandura / Carl Rogers 等）の小さな添え書きは**廃止**。概念名（自己効力感・島皮質 等）を**大きな主役ラベル**にする。人名を出すなら本文ラベルと同じ大きさで1つだけ、または省略してよい。
- **吹き出し・箇条書きは最大3つ**、各1〜数語（文章にしない）。長いキャプションは短い断定文（**全角16字以内目安**）に圧縮。
- **基本単位は「アイコン＋大きな単語」**。文章で説明しない。
- **検証**：コンタクトシート（1枚を幅480px程度に縮小）で全文字が読めればスマホ可読とみなす。読めない文字があるスライドは語数を減らして作り直す。

---

## 4. HiggsField 共通プロンプト前文（全スライド共通の冒頭ブロック）

`generate_image` model=`nano_banana_pro`、aspect_ratio `16:9`。各スライドのプロンプトはこの前文＋型別の作画指示（→ diagram_archetypes.md）で構成する。

```
A clean, editorial line-art infographic illustration in the style of a gentle academic
textbook figure (NOT watercolor, NOT 3D CG, NOT glowing sci-fi). 16:9. Thin even
dark-indigo outlines (#2E3A59), soft sky-blue fills used sparingly, ONE magenta-pink
(#FF4D88) accent. Sophisticated, intelligent, feminine-friendly, calm, lots of negative
space. Render Japanese with PERFECT accurate standard kanji.
READABILITY RULE (critical): ALL text must be VERY LARGE and BOLD — easily readable on a
small smartphone screen by a middle-aged viewer. Use as FEW words as possible so each can
be big. NO small text, NO fine print, NO tiny labels, NO researcher-name credits in small
type anywhere. Every label at least ~5% of frame height; the title much larger. Make
diagram labels (e.g. concept names) big and prominent, not tiny annotations. The title is
large but BALANCED with the body text, not oversized.
ADULT TONE (critical): refined, grown-up, calm — NOT cute/childish. Do NOT draw sparkles,
twinkles, glitter, stars, hearts, or magic wands. No fairy-tale/princess figures; any human
is a simple, natural line-art figure in plain clothing. Keep the friendly palette but never
make motifs childish.
KEY MESSAGE: put the conclusion line in a magenta-pink ROUNDED PILL (white bold text) around
72–82% height — keep this pink pill. But the very bottom ~15% stays empty, the SAME cream as
the top (the pill must sit above it).
BACKGROUND RULE: the ENTIRE background is ONE single uniform flat warm off-white (#F5F0E8)
from the very top edge to the very bottom edge — NO white band, NO white box, NO white
panel, NO gradient anywhere. Do NOT draw any subtitle bar or white rectangle. The bottom
15% stays free of graphics/text but the EXACT same off-white.
[ ↓ ここに型別の作画内容＋日本語テキスト（タイトル/ラベル/ピンクのキーメッセージ） ↓ ]
```

運用Tips：2K・1枚≈2クレジット・40〜90秒。複雑プロンプトは稀にハング→再投入。**日本語はliteralで書く**（unicodeエスケープは誤変換）。

---

## 5. 後処理パイプライン（scripts/slide_tools.py）

生成後は必ず機械処理で品質を担保する。順序：**whitefix → (必要なら stamp) → telopsafe → pptx**

| 処理 | コマンド | 目的 |
|---|---|---|
| 白箱除去 | `whitefix <in> <out>` | モデルが描く純白の箱/帯をクリーム地に置換（ピンク枠内の白文字は保護） |
| 金番号合成 | `stamp <in> <out> --num 01` | 章番号を全スライド同一デザイン（Didot中抜き金）で合成 |
| テロップ余白 | `telopsafe <in> <out>` | 84%縮小＋同色余白で下部15%を確実に空ける |
| PPTX化 | `pptx <dir> <out.pptx>` | 16:9フルブリード |
| 検査 | `audit <dir>` | 下部余白が確保されているか自動チェック |

---

## 6. ハマりどころと対策（Y-007で実証済み）

| 症状 | 原因 | 対策 |
|---|---|---|
| 下部に純白の箱・帯が出る | モデルが「字幕枠」を白で描く | `whitefix` で除去（プロンプトのBACKGROUND RULEだけでは防ぎきれない） |
| 下部15%に内容が食い込む | 「空けて」指示を守らない | `telopsafe` で機械的に確保 |
| 章番号01/02/03の字形がバラバラ | 生成のたびに揺れる | **番号は画像に焼かず**、左上を空けて生成→ `stamp` で統一合成 |
| 番号と見出しが重なる | 見出しが長い1行 | 見出しを2行＋「左20%を空ける」と指示してから stamp |
| 漢字が崩れる（例：寄） | nano_banana の文字精度 | 生成物を必ず目視、崩れたスライドだけ再生成（プロンプトに "PERFECT accurate kanji"） |
| クライアント不要の文字を消したい | 研究者名等 | HiggsField再生成より、PILで局所消去（円検出→弧の外側クリア→線の引き直し 等）が確実 |
| 画像に英単語が漏れる（例「LARGE」） | 英単語(LARGE/BIG等)を**ラベルの直前に**書いた | サイズ指示は冒頭のREADABILITY行に集約し、各ラベル直前に英単語を置かない。「Do NOT render any English words」を添える |

---

## 7. 成果物フォルダ規約

```
projects/Y-0XX_<topic>/
  スライド作成指示書.md          # 本規格を参照する案件別の割当表
  refs/original_script.txt       # 元台本
  slides/                        # 生成原本（番号合成済み）
    _raw/                        # HiggsField DL直後
    telop_safe/                  # 余白確保・PPTX用
    _archive/                    # 不採用・崩れ
  Y-0XX_<topic>_スライドNN枚.pptx
```
