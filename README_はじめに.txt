# NOIR ROUGE — iPhone対応・Private夢創作サイト

## できること
- スマホ幅に対応した3つの夢ページ
- ☆ マジェスティック☆マジョリカル：シェル・セレスタイト × ミア
- ♡ ハズビン・ホテル：エンジェル・ダスト × ルナ
- ○ ポケモン：N × アスカ
- ログインした招待ユーザーだけが閲覧可能
- 管理者だけが文章・画像を投稿、編集、削除可能
- 各ページのメイン画像を個別に設定可能
- 画像は非公開Supabase Storageに保存し、ログイン後に期限付きURLで表示

## 重要：Private設定について
GitHub Pages自体には閲覧者制限がありません。このサイトでは、ページを開いた時点ではログイン画面だけを表示し、投稿データと画像はSupabaseの認証・RLSで保護します。
ただし、GitHub Pages上のHTML/CSS/JavaScriptファイルそのものは公開リポジトリから見られます。サイトのソースコードまで非公開にしたい場合は、GitHub Pagesではなくアクセス制御付きホスティングが必要です。秘密の個人情報はサイトに掲載しないでください。

## セットアップ（最初だけPCまたはiPhoneブラウザで設定）
### 1. Supabaseプロジェクトを作る
1. https://supabase.com/ でアカウントを作成し、New projectを選びます。
2. プロジェクト名は `noir-rouge` など任意。データベースのパスワードは安全な場所に保管。
3. Project Settings → API（または API Keys）から Project URL と anon / publishable key を控えます。
4. Authentication → Users から管理者アカウントを作成します。管理者メールアドレスとパスワードを控えます。
5. 閲覧を許可する人も Authentication → Users から招待・作成します。公開サインアップは有効にしないでください。

### 2. データベースと非公開画像領域を作る
1. SupabaseのSQL Editorを開きます。
2. `schema.sql` の `YOUR_OWNER_EMAIL` を管理者のメールアドレスに置き換えます（2か所以上あります）。
3. SQL全体を貼り付けてRunします。
4. Authentication → Settingsで、必要に応じてメール確認を有効にします。招待ユーザーがログインできる状態にしてください。

### 3. サイトの接続情報を入れる
1. `config.js` を開きます。
2. `YOUR_SUPABASE_PROJECT_URL` をProject URLに置換。
3. `YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY` をanon / publishable keyに置換。
4. `YOUR_OWNER_EMAIL` を管理者メールアドレスに置換。
5. **service_role / secret keyは絶対に入力しないでください。**

### 4. GitHub Pagesへ公開
1. GitHubの `My_n` リポジトリを開きます。
2. `index.html` と `config.js` をリポジトリ直下にアップロード（既存のindex.htmlは置き換え）。
3. `Settings → Pages → Build and deployment` で `Deploy from a branch`、Branchを `main`、Folderを `/(root)` にしてSave。
4. 表示されたPages URLを開き、管理者アカウントでログインします。

## 投稿の使い方
- ログイン後、管理者アカウントではページ下部に「THE OWNER'S DESK」が表示されます。
- 投稿先を選び、文章と画像を選択して `PUBLISH POST`。
- 各投稿のEDIT / DELETEで編集・削除できます。
- 各ページのHERO IMAGE SETTINGSから、そのページ専用のメイン画像を設定できます。
- 閲覧者アカウントでは投稿・管理画面は表示されません。

## メモ
- 画像アップロード上限は10MBです。JPEG / PNG / WebP / GIFに対応。
- この構成はGitHub PagesとSupabaseの無料枠で始められますが、各サービスの利用条件・上限は変更される場合があります。
- 作品画像・キャラクター画像を使う場合は、権利者の利用条件を確認してください。
