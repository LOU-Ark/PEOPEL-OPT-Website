# PEOPEL-OPT-Website (PEOPEL-OPT Project)

このプロジェクトは、Gemini（各種モデル）を活用して法人格（Purpose/Mission/Vision）の策定からサイトマップ・コンテンツ戦略の策定、そして最終的なモダンでレスポンシブな単一HTMLページの生成までを自動化するワークフローです。

ディレクトリ構成と各ファイルの役割は以下の通りです。

- peopel-opt-project/
  - data/
    - myoponion.txt : 非構造化テキスト（企業の哲学・ビジョン）
  - src/
    - utils.py : 環境変数の読み込み、Geminiクライアント初期化、出力ディレクトリ処理
    - identity_generator.py : 法人格とサイト戦略の生成（Gemini 2.5 Flash想定）
    - html_generator.py : 各ページのHTML生成（Gemini 2.5 Pro想定）
  - .env.example : 環境変数テンプレート
  - main.py : ワークフロー統括スクリプト
  - MyHPwithGemini.ipynb : ノートブック実行ガイド（対話実行用）

使用方法（概要）
1. `.env` を作成して API キー等を設定する（`.env.example` を参照）
2. `python -m venv .venv && . .venv/bin/activate` 等で仮想環境を用意
3. 必要なパッケージをインストール（requirements.txt を追記する場合があります）
4. `python main.py` を実行すると以下の処理が順に行われます：
   - data/myoponion.txt から原文を読み込み
   - identity_generator により法人格 / サイトマップ / コンテンツ骨子 / ページ一覧(JSON) を生成
   - html_generator により各ページの HTML を生成
   - 出力ディレクトリをクリーンにし、生成結果を保存、ZIP アーカイブ作成

注意
- 実際の API 呼び出し部分はダミー実装／プレースホルダになっています。API クライアントを用いてプロンプトのやり取りを実装してください。
- Gemini（Pro / Flash）などモデルの利用は、APIキーやモデル名を `.env` に設定して切り替える仕組みを想定しています.
