# 投資診断サイト構築仕様書 v1.0

## 📋 概要

この仕様書は、投資に興味を持ってもらうための「◯◯診断」サイトを、ターゲットに合わせて自動生成するためのテンプレートです。

---

## 🎯 ターゲット定義

> **【指示】** 以下の項目を埋めてください。未指定の場合はデフォルト値を使用します。

```yaml
target:
  # 必須：メインターゲット
  persona: ""  # 例：「20代女性」「30代会社員」「大学生」「主婦」「シニア層」
  
  # 任意：詳細属性
  age_range: ""        # 例：「20-25歳」「35-45歳」
  gender: ""           # 例：「女性」「男性」「指定なし」
  occupation: ""       # 例：「会社員」「学生」「フリーランス」「主婦/主夫」
  income_level: ""     # 例：「〜300万」「300-500万」「500万〜」
  investment_experience: ""  # 例：「未経験」「初心者」「中級者」
  
  # 任意：興味・関心
  interests: []        # 例：["推し活", "旅行", "ゲーム", "美容", "子育て"]
  pain_points: []      # 例：["将来が不安", "貯金ができない", "投資が怖い"]
  goals: []            # 例：["老後資金", "旅行資金", "FIRE"]
```

---

## 🎨 デザインシステム

### デザインテーマ選択

ターゲットに応じて最適なテーマを選択してください。

| テーマID | テーマ名 | 適合ターゲット | 特徴 |
|---------|---------|---------------|------|
| `cute` | キュート・ポップ | 10-20代女性 | パステルカラー、丸みのあるUI、絵文字多用 |
| `minimal` | ミニマル・クリーン | 20-30代男女 | 白基調、余白多め、洗練されたタイポグラフィ |
| `premium` | プレミアム・ラグジュアリー | 30-40代高収入層 | ダーク基調、ゴールドアクセント、高級感 |
| `friendly` | フレンドリー・カジュアル | 20-30代全般 | 明るい配色、親しみやすいイラスト |
| `professional` | プロフェッショナル | 30-50代ビジネス層 | ネイビー基調、信頼感、データビジュアル |
| `playful` | ゲーミフィケーション | 10-20代、ゲーム好き | ネオンカラー、アニメーション多め、RPG風 |
| `natural` | ナチュラル・オーガニック | 30-40代女性 | アースカラー、手書き風フォント |
| `retro` | レトロ・ノスタルジック | 30-40代 | ヴィンテージ配色、クラシックなUI |

### カラーパレット定義

```yaml
color_palette:
  # テーマに応じて自動選択、またはカスタム指定
  primary: ""      # メインカラー
  secondary: ""    # サブカラー
  accent: ""       # アクセントカラー
  background: ""   # 背景色
  text: ""         # テキスト色
  
  # グラデーション（オプション）
  gradient:
    start: ""
    end: ""
    direction: ""  # "to-r", "to-br", "to-b" など
```

### タイポグラフィ

```yaml
typography:
  # 日本語フォント
  heading_font: ""  # 見出し用：例「Noto Sans JP」「M PLUS Rounded 1c」「Zen Maru Gothic」
  body_font: ""     # 本文用
  
  # フォントウェイト
  heading_weight: "" # 例：「900」「700」「600」
  body_weight: ""    # 例：「400」「500」
  
  # フォントサイズスケール
  size_scale: ""     # 「compact」「normal」「large」
```

### アニメーション・インタラクション

```yaml
animation:
  level: ""         # 「minimal」「moderate」「rich」
  
  # 具体的な設定
  page_transition: ""    # 「fade」「slide」「scale」
  button_hover: ""       # 「scale」「glow」「bounce」
  progress_bar: ""       # 「smooth」「stepped」「animated」
  result_reveal: ""      # 「fade-up」「bounce」「confetti」
```

---

## 🧩 コンポーネント構成

### 1. スタート画面

```yaml
start_screen:
  # ヘッダー
  logo:
    type: ""           # 「emoji」「icon」「image」「text」
    content: ""        # ロゴの内容
  
  # メインビジュアル
  hero:
    title: ""          # 診断タイトル（ターゲットに響く表現）
    subtitle: ""       # サブタイトル
    description: ""    # 説明文（2-3行）
  
  # キャラクター/タイプ プレビュー
  type_preview:
    show: true         # プレビュー表示の有無
    style: ""          # 「grid」「carousel」「stack」
  
  # メタ情報
  meta:
    question_count: 7  # 質問数
    estimated_time: "2分"
  
  # CTA
  cta_button:
    text: ""           # 例：「診断スタート」「はじめる」
    style: ""          # 「gradient」「solid」「outline」
```

### 2. 質問画面

```yaml
question_screen:
  # プログレス表示
  progress:
    type: ""           # 「bar」「dots」「fraction」「none」
    show_percentage: true
  
  # 質問カード
  question_card:
    layout: ""         # 「center」「left」「card」
    number_display: "" # 「badge」「inline」「none」
  
  # 選択肢
  options:
    layout: ""         # 「vertical」「grid-2」「grid-2x2」
    style: ""          # 「card」「button」「radio」
    icon_position: ""  # 「left」「top」「none」
  
  # フィードバック
  selection_feedback:
    type: ""           # 「highlight」「check」「animate」
    delay_ms: 500      # 次の質問への遷移時間
```

### 3. 結果画面

```yaml
result_screen:
  # 結果ヘッダー
  header:
    pre_text: ""       # 例：「あなたの投資タイプは...」
    reveal_animation: "" # 「bounce」「fade」「typewriter」
  
  # タイプ表示
  type_display:
    icon_size: ""      # 「small」「medium」「large」「xlarge」
    show_title: true
    show_subtitle: true
  
  # 詳細セクション（表示順序も指定可能）
  sections:
    - type: "description"
      title: ""
    - type: "strengths"
      title: "あなたの強み"
      icon: "💪"
    - type: "weaknesses"      # オプション
      title: "気をつけるポイント"
      icon: "⚠️"
    - type: "advice"
      title: "アドバイス"
      icon: "💡"
    - type: "recommendations"
      title: "おすすめの投資"
      icon: "📈"
    - type: "compatibility"   # オプション：相性の良いタイプ
      title: "相性の良いタイプ"
      icon: "🤝"
  
  # アクションボタン
  actions:
    share:
      enabled: true
      platforms: ["twitter", "line", "copy"]
      text_template: ""
    retry:
      enabled: true
      text: ""
    cta:
      enabled: true
      text: ""
      url: ""
  
  # フッターCTA
  footer_cta:
    enabled: true
    title: ""
    description: ""
    button_text: ""
    button_url: ""
```

---

## 📝 質問設計ガイドライン

### 質問カテゴリ

各診断には以下のカテゴリから質問を構成してください。

```yaml
question_categories:
  # 投資行動系（必須：2-3問）
  investment_behavior:
    - "資金の使い方"
    - "リスクへの反応"
    - "情報収集方法"
    - "投資判断基準"
  
  # 性格・価値観系（必須：2-3問）
  personality:
    - "意思決定スタイル"
    - "時間軸の考え方"
    - "目標設定の仕方"
  
  # ライフスタイル系（任意：1-2問）
  lifestyle:
    - "休日の過ごし方"
    - "買い物の仕方"
    - "趣味・関心"
```

### 質問テンプレート

```yaml
question_template:
  id: 1
  category: ""           # 上記カテゴリから選択
  question: ""           # 質問文（ターゲットに合わせた言葉遣い）
  
  options:
    - text: ""           # 選択肢テキスト
      scores:            # 各タイプへのスコア配分（0-3）
        type_a: 0
        type_b: 0
        type_c: 0
        type_d: 0
    # ... 4つの選択肢
```

### ターゲット別 質問文スタイル

| ターゲット | 文体 | 語尾 | 例 |
|-----------|------|------|-----|
| 10-20代女性 | カジュアル | 〜？ / 〜かな？ | 「臨時収入ゲット！どう使う？」 |
| 20-30代男性 | フランク | 〜？ / 〜だ？ | 「ボーナス30万、何に使う？」 |
| 30-40代全般 | 丁寧 | 〜ですか？ | 「臨時収入があった場合、どのように使いますか？」 |
| シニア層 | フォーマル | 〜でしょうか？ | 「まとまった資金が入った際、どのようにお使いになりますか？」 |

---

## 🦁 診断タイプ設計

### タイプ定義テンプレート

```yaml
investor_types:
  type_a:
    id: ""              # 内部ID
    name: ""            # タイプ名（例：「ライオン型」）
    emoji: ""           # 絵文字/アイコン
    title: ""           # キャッチコピー（例：「攻めのアグレッシブ投資家」）
    
    # ビジュアル
    visual:
      primary_color: ""
      gradient: ""
      background: ""
      border_color: ""
      
    # コンテンツ
    content:
      description: ""   # 100-150文字の説明
      strengths: []     # 3つの強み
      weaknesses: []    # 2-3つの弱点（オプション）
      advice: ""        # 50-80文字のアドバイス
      
    # 投資関連
    investment:
      recommended: []   # おすすめ投資商品（3つ）
      risk_tolerance: "" # 「高」「中」「低」
      time_horizon: ""   # 「短期」「中期」「長期」
      
    # 追加情報（オプション）
    extra:
      famous_investor: ""  # 似ている有名投資家
      compatible_types: [] # 相性の良いタイプ
      percentage: ""       # 「全体の約◯%」
```

### タイプ命名ガイドライン

| パターン | 例 | 適合ターゲット |
|---------|-----|---------------|
| 動物型 | ライオン、カメ、フクロウ | 全般（親しみやすい） |
| 職業型 | トレーダー、銀行員、研究者 | ビジネス層 |
| キャラクター型 | 勇者、魔法使い、賢者 | ゲーム好き・若年層 |
| 色/宝石型 | ゴールド、シルバー、エメラルド | 女性向け・高級感 |
| 食べ物型 | ステーキ派、煮込み派、サラダ派 | カジュアル・親しみやすさ |
| 星座/属性型 | 火属性、水属性、風属性 | スピリチュアル好き |

---

## 🔧 技術仕様

### フレームワーク

```yaml
tech_stack:
  framework: "React"
  styling: "Tailwind CSS"
  state_management: "useState (React Hooks)"
  animations: "CSS Transitions + Tailwind"
```

### レスポンシブ対応

```yaml
responsive:
  mobile_first: true
  breakpoints:
    sm: "640px"
    md: "768px"
    lg: "1024px"
  
  # モバイル最適化
  mobile:
    touch_targets: "min 44px"
    font_size_base: "16px"
    padding: "16px"
```

### パフォーマンス

```yaml
performance:
  # 画像最適化
  images:
    format: "webp"
    lazy_loading: true
  
  # アニメーション
  animations:
    prefer_css: true
    reduce_motion_support: true
```

---

## 📱 SNSシェア設定

```yaml
share:
  # シェアテキストテンプレート
  text_template: |
    私の投資家タイプは「{emoji} {type_name}」でした！
    {title}
    
    {hashtag}
  
  # ハッシュタグ
  hashtags:
    - "#投資家診断"
    - "#投資初心者"
    # ターゲット別追加タグ
  
  # OGP設定
  ogp:
    title: ""
    description: ""
    image: ""
```

---

## 📊 コンバージョン設計

### CTA配置

```yaml
conversion:
  # 結果画面CTA
  result_cta:
    primary:
      text: ""           # 例：「口座開設はこちら」
      url: ""
      style: "prominent"
    secondary:
      text: ""           # 例：「投資の始め方を学ぶ」
      url: ""
  
  # 追加導線
  additional:
    - type: "article"    # 関連記事への誘導
      title: ""
      url: ""
    - type: "simulation" # シミュレーターへの誘導
      title: ""
      url: ""
```

---

## 🚀 生成プロンプト

以下のフォーマットで生成AIに指示してください：

```
この仕様書に基づいて、投資診断サイトを作成してください。

【ターゲット】
{ここにターゲットを記入}
例：「20代後半〜30代前半の女性、投資未経験、推し活や旅行が趣味」

【追加要件】（任意）
- デザインテーマ：{テーマID}
- 診断タイプ：{動物型/職業型/など}
- 特に強調したいポイント：{例：SNSシェアしやすさ}
- 質問数：{5-10問}

【出力形式】
- React (JSX) 単一ファイル
- Tailwind CSS使用
- 日本語UI
```

---

## 📋 チェックリスト

生成後、以下を確認してください：

### デザイン
- [ ] ターゲットに適したカラーパレットか
- [ ] フォントサイズは読みやすいか
- [ ] モバイルで操作しやすいか
- [ ] アニメーションは適切か

### コンテンツ
- [ ] 質問文はターゲットの言葉遣いか
- [ ] 選択肢は4つ均等にバランスが取れているか
- [ ] 結果の説明は共感を得られる内容か
- [ ] アドバイスは実用的か

### 機能
- [ ] 全質問に回答できるか
- [ ] 結果が正しく計算されるか
- [ ] シェア機能は動作するか
- [ ] リトライ機能は動作するか

### コンバージョン
- [ ] CTAは目立つ位置にあるか
- [ ] 次のアクションが明確か

---

## 📎 付録：ターゲット別プリセット例

### プリセット A：20代女性・推し活層

```yaml
preset_a:
  target: "20代女性、推し活が趣味、投資未経験"
  theme: "cute"
  type_naming: "動物型（かわいい系）"
  color_palette:
    primary: "#FF6B9D"
    secondary: "#C084FC"
    accent: "#FCD34D"
  tone: "カジュアル・絵文字多め"
  cta_focus: "推し活資金を増やす"
```

### プリセット B：30代男性・会社員

```yaml
preset_b:
  target: "30代男性会社員、投資初心者、将来の資産形成に関心"
  theme: "minimal"
  type_naming: "職業型"
  color_palette:
    primary: "#3B82F6"
    secondary: "#1E293B"
    accent: "#10B981"
  tone: "フランク・データ重視"
  cta_focus: "効率的な資産形成"
```

### プリセット C：40代・資産形成本格化層

```yaml
preset_c:
  target: "40代男女、ある程度の貯蓄あり、本格的な投資を検討"
  theme: "premium"
  type_naming: "宝石型"
  color_palette:
    primary: "#1E293B"
    secondary: "#D4AF37"
    accent: "#F8FAFC"
  tone: "丁寧・専門的"
  cta_focus: "ポートフォリオ最適化"
```

---

## 更新履歴

| バージョン | 日付 | 変更内容 |
|-----------|------|---------|
| 1.0 | 2025-01-XX | 初版作成 |

---

*この仕様書は継続的に改善されます。フィードバックをお待ちしています。*
