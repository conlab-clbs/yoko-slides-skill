# yoko-slides — やさしい学術教科書スライド 制作スキル

葉子チャンネル（Y-シリーズ／心理学×AI波動「ロジカル願望実現メソッド」）の動画台本にある
**「スライド設計リスト」** から、梅﨑さん好評の **「やさしい学術教科書」テイストのクリーン線画スライド** を
HiggsField (Nano Banana Pro) で一気通貫制作する Claude Code 用スキルです。

台本番号を渡すと、**台本解析 → 図解の型割当 → プロンプト生成 → 画像生成 → 白箱除去 → テロップ余白確保 →
（章番号の金スタンプ）→ 16:9 フルブリード PPTX** までを自動で行います。

```
/yoko-slides 008
```

## 含まれるもの

| ファイル | 役割 |
|---|---|
| `SKILL.md` | スキル本体（ワークフロー・トリガー） |
| `reference/master_design_spec.md` | ① 共通デザイン規格（**水彩禁止**・パレット・4ゾーン・**可読性ルール**・共通プロンプト前文・ハマりどころ） |
| `reference/diagram_archetypes.md` | ② 図解の型ライブラリ（A〜I）＋型別プロンプト |
| `scripts/slide_tools.py` | ③ 後処理 CLI（whitefix / telopsafe / stamp / pptx / audit） |

## デザイン要点（やさしい学術教科書）

- クリーンな**線画イラスト**（見本＝セリグマン犬の実験スライド）。**水彩タッチ／暗いCG／写真・3Dは禁止**
- 生成り地 #F5F0E8 ／ インディゴ線 #2E3A59 ／ スカイブルー面 #C5E0F0 ／ 差し色ピンク #FF4D88 ／ 章番号のみ金 #C9A14A
- **スマホ縦・最小表示で中高年女性が読める大きさ**を絶対基準（語数を削り、全文字を大きく。研究者名等の fine print は禁止）
- 下部15%はテロップ専用に空ける（背景色は上下とも同一フラット）

## 導入方法（社内メンバー向け）

Claude Code のユーザースキルとして配置します。

```bash
git clone <このリポジトリのURL> ~/.claude/skills/yoko-slides
```

すでに `~/.claude/skills/` がある前提です。配置後、Claude Code を再起動すると `/yoko-slides` が使えます。

### 前提ツール
- **HiggsField MCP**（`generate_image` model=`nano_banana_pro` が使えること）
- Python: `pillow`, `numpy`, `python-pptx`
- 金番号合成・日本語描画に macOS 標準フォント（Didot / ヒラギノ角ゴシック）を使用（パスは `scripts/slide_tools.py` 上部で変更可）

## 後処理ツールの使い方（単体）

```bash
S=~/.claude/skills/yoko-slides/scripts/slide_tools.py
python3 "$S" whitefix  raw/ clean/      # 純白の箱/帯をクリーム地に置換（ピンク枠内の白文字は保護）
python3 "$S" stamp     in.png out.png --num 01   # 統一デザインの金番号を合成
python3 "$S" telopsafe clean/ final/    # 84%縮小＋同色余白で下部15%を確保
python3 "$S" pptx      final/ deck.pptx # 16:9 フルブリード PPTX
python3 "$S" finish    raw/ final/ deck.pptx     # whitefix→telopsafe→pptx 一括
python3 "$S" audit     final/           # 下部テロップ余白の自動チェック
```

## 実績
- Y-007「量子もつれと引き寄せの法則」（18枚）
- Y-008「『いい人』を止めて自分軸に変わる3つの習慣」（24枚）

## 対象外
- 台本そのものの執筆（別スキル）
- 暗いネイビーCG系（量子脳コーチ3Days等）
