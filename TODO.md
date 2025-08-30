# TODO: `gl-doc` 開発実行計画

このドキュメントは、`progress.json` を管理するための新しいCLIツール `gl-doc` の開発に関する実行計画をまとめたものです。

## 1. ユーザーの要望

- `progress.json` の状態管理（生成、更新、読み取り）を行うCLIツールを開発する。
- 開発言語として、型安全性とエラーハンドリングに優れた **Rust** を採用する。
- ツールの名称は **`gl-doc`** とする。
- `gl-doc` ツール自体に、関連するGeminiカスタムコマンドファイル（`.toml`群）をユーザーのプロジェクトに **インストール（配布）する機能** を含める。

## 2. 分析結果のまとめ

- Rustの採用は、`serde`による厳密な型定義、`Result`による堅牢なエラーハンドリング、依存関係のない単一バイナリ配布といった点で、提案された要件に最適である。
- シェルスクリプト案に比べて、長期的な保守性、信頼性、拡張性が大幅に向上する。
- コマンドインストール機能は、ツールのポータビリティを高め、利用者がワークフロー全体を容易にセットアップできるようにするための優れた機能改善である。

## 3. 詳細な実行計画

### ステップ 1: Rustプロジェクトのセットアップ

1.  `cargo new gl-doc` を実行し、新しいRustプロジェクトを作成する。
2.  `gl-doc/Cargo.toml` に以下のクレート（依存ライブラリ）を追加する。
    ```toml
    [dependencies]
    clap = { version = "4.5", features = ["derive"] }
    serde = { version = "1.0", features = ["derive"] }
    serde_json = "1.0"
    anyhow = "1.0"
    include_dir = { version = "0.7", features = ["zip"] }
    chrono = { version = "0.4", features = ["serde"] }
    ```

### ステップ 2: データ構造の定義 (`src/state.rs`)

1.  `progress.json` のスキーマに対応するRustの構造体を定義する (`struct Progress`, `struct Approvals`, `struct TaskProgress` など)。
2.  すべての構造体に `serde` の `Serialize`, `Deserialize` を派生させる。
3.  状態を更新するためのメソッド（例: `fn set_phase(&mut self, new_phase: &str)`)を構造体に実装し、ロジックをカプセル化する。

### ステップ 3: CLIインターフェースの定義 (`src/cli.rs`)

1.  `clap` を使い、`gl-doc` のサブコマンド、オプション、引数を定義する。
2.  実装するサブコマンド:
    - `install`: カスタムコマンド群をインストールする。
    - `init`: `progress.json` を初期化する。
    - `set`: `phase` などの値を設定する。
    - `approve`: ドキュメントを承認済みにする。
    - `task`: 個別タスクの状態を操作する。
    - `status`: 現在の進捗を表示する。

### ステップ 4: 本体ロジックの実装 (`src/main.rs`)

1.  `main`関数で、`cli.rs`で定義したCLI引数をパースする。
2.  各サブコマンドに対応する処理を実装する。基本的な流れは以下の通り。
    a. `progress.json` ファイルを読み込む。
    b. `serde_json` を使って `Progress` 構造体にデシリアライズする。
    c. 構造体のメソッドを呼び出して状態を更新する。
    d. 更新された構造体をJSON文字列にシリアライズする。
    e. 新しいJSON文字列を `progress.json` に書き込む。
3.  `anyhow` を用いて、ファイルI/Oや(デ)シリアライズ時のエラーを適切にハンドリングする。

### ステップ 5: コマンドインストール機能の実装

1.  `gl-doc` プロジェクト内に `assets/commands/spec` ディレクトリを作成する。
2.  既存の `.gemini/commands/spec/*.toml` ファイルをすべて `assets/commands/spec` にコピーする。
3.  `include_dir` クレートを使い、`assets` ディレクトリをコンパイル後のバイナリに埋め込む。
4.  `install` サブコマンドのロジックとして、埋め込まれたディレクトリの内容を、コマンド実行カレントディレクトリ下の `.gemini/commands/spec/` に展開する処理を実装する。

### ステップ 6: Geminiカスタムコマンドの更新

1.  プロジェクトルートの `.gemini/commands/spec/*.toml` ファイルを一つずつ修正する。
2.  `progress.json` を直接操作している `replace` ツールの呼び出しを、`run_shell_command` を使って `gl-doc` の適切なサブコマンド（例: `gl-doc set phase --feature {{args}} design-generated`）を呼び出すように置き換える。

### ステップ 7: ビルドと検証

1.  `gl-doc` ディレクトリで `cargo build --release` を実行し、リリースビルドを行う。
2.  生成されたバイナリ (`gl-doc/target/release/gl-doc`) を使って、各サブコマンドが意図通りに動作するか手動でテストする。
3.  更新されたGeminiカスタムコマンド（例: `/doc:create`）を実行し、`gl-doc` が正しく呼び出されることを確認する。

## 4. 影響があるおよび更新対象のファイルとディレクトリ一覧

### 新規作成

- `TODO.md` (このファイル)
- `gl-doc/` (Rustプロジェクトディレクトリ)
  - `gl-doc/Cargo.toml`
  - `gl-doc/.gitignore`
  - `gl-doc/src/main.rs`
  - `gl-doc/src/cli.rs`
  - `gl-doc/src/state.rs`
  - `gl-doc/assets/commands/spec/*.toml` (全カスタムコマンドのコピー)

### 更新対象

- `.gemini/commands/spec/create.toml`
- `.gemini/commands/spec/define.toml`
- `.gemini/commands/spec/design.toml`
- `.gemini/commands/spec/fail.toml`
- `.gemini/commands/spec/improve.toml`
- `.gemini/commands/spec/manual.toml`
- `.gemini/commands/spec/pass.toml`
- `.gemini/commands/spec/requirements.toml`
- `.gemini/commands/spec/status.toml`
- `.gemini/commands/spec/steering-apply.toml`
- `.gemini/commands/spec/tasks.toml`
- `.gemini/commands/spec/testcase.toml`
