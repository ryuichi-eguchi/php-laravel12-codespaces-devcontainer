# Laravel 12 開発環境 (PHP 8.3 & MariaDB) for GitHub Codespaces

このリポジトリは、**GitHub Codespaces** で **PHP 8.3** をベースにした **Laravel 12** の開発環境を簡単に構築できるようにするための設定を提供します。  
**MariaDB** を使用し、Docker を活用した開発環境を即座にセットアップできます。

---

## 🚀 GitHub Codespaces でのセットアップ手順

### 1️⃣ Codespaces を起動

1. GitHub の **このリポジトリ** を開く  
2. `<> Code` ボタンをクリック  
3. `Codespaces` タブから `Create Codespace on main` を選択  

Codespaces のセットアップが完了すると、開発環境が自動的に構築されます。

---

### 2️⃣ Laravel 12 の環境構築

Codespaces が起動したら、ターミナルで以下のコマンドを順番に実行します。

#### 🔹 2-1. Laravel プロジェクトの作成

```bash
composer create-project laravel/laravel:^12 laravel-app
cd laravel-app
```

#### 🔹 2-2. 環境設定 (.env ファイルの更新)

`.env` ファイルを編集し、MariaDB の接続情報を更新します。

```dotenv
DB_CONNECTION=mysql
DB_HOST=mariadb
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=secret
```

#### 🔹 2-3. アプリケーションキーの生成

```bash
php artisan key:generate
```

#### 🔹 2-4. データベースマイグレーション

```bash
php artisan migrate
```

#### 🔹 2-5. サーバーの起動

```bash
php artisan serve --host=0.0.0.0 --port=8080
```

ポップアップが出てくるのでブラウザで開くを押して、別タブを開いてください。

---

## 🛠 MariaDB コマンドラインツールの利用

MariaDB クライアントがインストールされているため、以下のコマンドで MariaDB に接続できます。

```bash
mysql -h mariadb -uroot -p
```

パスワードの入力を求められたら、`.env` に設定したパスワード（例: `secret`）を入力してください。

---

## 🔍 Codespaces 用の追加情報

### ✅ `.devcontainer` 設定

このリポジトリには **GitHub Codespaces 用の `.devcontainer` 設定** が含まれています。  
これにより、Codespaces を起動すると **自動で開発環境が構築される** 仕組みになっています。

### ✅ Git の利用

Codespaces には Git がインストールされているため、通常の Git コマンドが利用可能です。

```bash
git add .
git commit -m "Update project"
git push origin main
```
