# AWS ECR Deploy Template

GitHub ActionsからOIDC認証を用いてAmazon ECRへコンテナイメージを自動ビルド＆プッシュする汎用テンプレートです。

## セットアップ手順

1. **AWS初期設定（初回のみ）**
   - `setup-aws.yml` を AWS CloudFormation にアップロードしてスタックを作成します。
   - パラメータ `GitHubOwner` に自身のGitHubアカウント名を入力します。

2. **GitHubリポジトリの設定**
   - リポジトリの **Settings > Secrets and variables > Actions > Variables** を開きます。
   - `AWS_ACCOUNT_ID` に自身の12桁のAWSアカウントIDを登録します（必要に応じて `AWS_REGION` も登録、デフォルトは `ap-northeast-1`）。

3. **利用方法**
   - `app` 配下等にアプリコードを配置し、`main` ブランチへプッシュするだけで、リポジトリ名と同名のECRリポジトリへ自動配備されます。
