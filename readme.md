# ETC Expense Checker

ETC利用明細から通勤区間を除外し、業務利用分のみを抽出するWebアプリケーション

## 概要

従業員から提出されるETC利用明細CSVファイルを読み込み、事前に設定した通勤区間の利用を自動的に除外することで、業務利用分のみを抽出できるツールです。経費精算の効率化に役立ちます。

## デモ

[https://{username}.github.io/etc-expense-checker/](https://{username}.github.io/etc-expense-checker/)

## 機能

- **CSVファイル読み込み**
  - GitHubリポジトリからの自動読み込み
  - ローカルファイルのアップロード
  - Shift-JISエンコーディング対応

- **通勤区間設定**
  - 複数の通勤ルート登録可能
  - 双方向の移動を自動認識

- **データ処理**
  - 通勤利用と業務利用の自動判定
  - 件数・金額の集計表示
  - 業務利用率の算出

- **エクスポート機能**
  - 業務利用分のみのCSVダウンロード
  - 元のフォーマットを維持

## 使い方

### 1. CSVファイルの準備

ETC利用明細のCSVファイルを準備します。以下の列を含む必要があります：
- 利用年月日（自）
- 時分（自）
- 利用ＩＣ（自）
- 利用ＩＣ（至）
- 通行料金
- 車両番号

### 2. 通勤区間の設定

1. 「通勤区間設定」セクションで出発ICと到着ICを入力
2. 複数の通勤ルートがある場合は「+ 通勤ルート追加」をクリック

### 3. データの読み込みと処理

**GitHubから読み込む場合：**
1. 「GitHubから自動読み込み」を選択
2. CSV URLを入力（デフォルト: `./data/etc-data.csv`）
3. 「読み込み」ボタンをクリック

**ローカルファイルの場合：**
1. 「ローカルファイルをアップロード」を選択
2. ファイルを選択またはドラッグ&ドロップ

### 4. 結果の確認とダウンロード

- 処理結果が表形式で表示されます
- 通勤利用分は赤色でハイライト
- 「通勤除外データをダウンロード」で業務利用分のみをCSV形式で保存

## セットアップ

### GitHub Pagesでの公開

1. このリポジトリをフォークまたはクローン
2. `data`フォルダにCSVファイルを配置（オプション）
3. リポジトリの Settings → Pages でGitHub Pagesを有効化
4. Source を "Deploy from a branch" に設定
5. Branch を "main" / "/ (root)" に設定

### ローカルでの実行

```bash
git clone https://github.com/{username}/etc-expense-checker.git
cd etc-expense-checker
# HTTPサーバーを起動（Python 3の場合）
python -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

## ファイル構成

```
etc-expense-checker/
├── index.html      # メインアプリケーション
├── data/           # CSVファイル配置用（オプション）
│   └── etc-data.csv
└── README.md       # このファイル
```

## 技術仕様

- **フロントエンド**: Vanilla JavaScript, HTML5, CSS3
- **CSVパース**: Papa Parse 5.3.0
- **文字エンコーディング**: Shift-JIS対応
- **ブラウザ要件**: モダンブラウザ（Chrome, Firefox, Safari, Edge）

## 注意事項

- CSVファイルにETC利用明細以外の個人情報が含まれないよう注意してください
- GitHub Pagesで公開する場合、CSVファイルも公開されることに注意してください
- プライベートなデータを扱う場合は、ローカルファイルアップロード機能を使用してください

## ライセンス

MIT License

## 作者

[Your Name]

## 貢献

Issue や Pull Request は歓迎します。大きな変更を加える場合は、まず Issue で議論してください。