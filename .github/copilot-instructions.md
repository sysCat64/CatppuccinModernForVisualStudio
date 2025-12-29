# Copilot Instructions (Catppuccin Modern for Visual Studio 2026)

## 言語設定

- **すべての応答は日本語で行うこと**（コード例の説明、エラーメッセージ、提案内容など）
- コード内のコメントも日本語で記述する
- ユーザーが英語で質問した場合でも、応答は日本語で返す
- 専門用語は必要に応じて英語を併記してもよい（例：「テーマ定義（.vstheme）」）

## プロジェクト概要

- Visual Studio 2026 向けの非公式 Catppuccin カラーパレットテーマ拡張（VSIX）。
- 4 種類のテーマ定義（Latte / Frappé / Macchiato / Mocha）を .vstheme で管理。
- 既定の VS テーマにフォールバックする前提で、編集/コア UI を中心に配色。

## 作業方針

- 既存パレットに忠実な配色を維持し、コントラストと可読性を優先。
- 変更時は影響範囲の小さい diff を心掛け、不要な生成物（bin/、obj/）は編集しない。
- 日本語/英語ともに簡潔な説明を添え、過剰なコメントは避ける。

## 主要ファイルと扱い

- テーマ定義: `Catppuccin*.vstheme`（Latte/Frappé/Macchiato/Mocha）。配色変更はこのファイルで行い、一貫性を保つ。
- VSIX マニフェスト: [source.extension.vsixmanifest](../source.extension.vsixmanifest)。ID/バージョン/説明/アイコン/タグの更新時は整合性を確認。
- ソリューション/プロジェクト: `CatppuccinModernForVisualStudio.slnx`, `CatppuccinModernForVisualStudio.csproj`。設定変更は最小限に。
- ドキュメント: [README.md](../README.md), [README.ja.md](../README.ja.md), [CHANGELOG.md](../CHANGELOG.md), [LICENSE.txt](../LICENSE.txt)。内容を更新する際は両言語の差分を意識。
- アセット: `images/` にプレビュー画像。追加時はパスと参照先を更新。

## ビルド/パッケージ

- 推奨: Visual Studio 2026 Preview でソリューションを開き Release ビルド → VSIX を生成。
- CLI 例: `msbuild CatppuccinModernForVisualStudio.csproj /t:Build /p:Configuration=Release`
- 出力は `bin/Release/` 配下。生成物はコミット対象外。

## テスト/検証

- VSIX をインストールし、`Tools > Options > Environment > General > Color theme` で各テーマが選択・適用できることを確認。
- エディタ文字色・背景のコントラスト、選択/差分表示、エラー/警告色、リンク色など視認性をチェック。
- 未定義トークンが既定テーマへフォールバックすることを念頭に、必要最小限の定義を追加。

## 変更ガイドライン

- 配色追加時は 4 テーマすべてで色の役割を揃える（例: コメント色の明度関係を一致）。
- 新しい UI/エディタ要素を定義する場合は VS 2026 のトークン名を確認し、影響箇所を明記。
- 説明文やメタデータ更新時はライセンス表記と非公式である旨を保持。

## レビュー観点

- 配色破綻（低コントラスト/過飽和）、テーマ間の不整合、トークン名の誤りがないか。
- マニフェストのバージョン/タグ/説明が変更内容と一致しているか。
- 生成物混入の有無、ドキュメントの整合性（英日両方）。

## Git コミットメッセージ方針

* コミットメッセージは **日本語** で記述する
* 形式は「簡潔な要約（50文字目安）」＋必要なら本文で詳細を補足
* Copilot が提案するコミットメッセージも日本語に統一する
* **PowerShell対応**: 複数行メッセージは `@"..."@` を使用、またはシングルラインを推奨

### 具体例

* **シングルライン（テーマ配色更新）**:
  ```
  git commit -m "全テーマのエラー警告色を調整"
  ```

* **シングルライン（マニフェスト/ドキュメント更新）**:
  ```
  git commit -m "バージョンを1.1へ更新、CHANGELOG追加"
  ```

* **マルチライン（複数ファイル修正 - PowerShell）**:
  ```powershell
  git commit -m @"
  全テーマのコメント色を統一

  CatppuccinLatte.vstheme、Frappe、Macchiato、Mocha で色の明度関係を調整。
  可読性とコントラストの向上を目的とした変更。
  "@
  ```

* **マルチライン（バージョンアップ時 - PowerShell）**:
  ```powershell
  git commit -m @"
  バージョン1.1へ更新

  テーマファイルのコメント色調整、マニフェストのバージョン更新、CHANGELOG記載。
  README 英日両版の表現を見直し。
  "@
  ```

### 注意事項

* `-` で始まる箇条書きはPowerShellでオプションと誤認されるため、マルチラインメッセージでは避けるか、`@"..."@` を使用すること
* 修正ファイルが複数テーマ共通の場合は「全テーマ」と明記する
* マニフェスト更新時はバージョン番号を記載する

