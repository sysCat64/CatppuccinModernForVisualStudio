# Catppuccin Modern for Visual Studio (Unofficial)

Catppuccin カラーパレットをベースにした  
**Visual Studio 2026 向けの非公式テーマ拡張機能**です。

本テーマは、Visual Studio 2026 のテーマ拡張機能仕様に対応する形で
個人的な利用目的から作成しました。

<p align="center">
   <a href="LICENSE.txtLICENSE"><img src="https://img.shields.io/static/v1.svg?style=for-the-badge&label=License&message=MIT&logoColor=d9e0ee&colorA=363a4f&colorB=b7bdf8"/></a>
</p>

---

## 概要

本拡張機能は、落ち着いたパステル調の配色で知られる  
[Catppuccin](https://catppuccin.com/) テーマを Visual Studio 2026 で利用できるようにしたものです。

- Visual Studio 2026対応
- Catppuccin の配色思想を尊重した設計
- 未定義トークンは Visual Studio 標準テーマへフォールバック

### プレビュー

#### Latte

<img src="./images/CatppuccinLatte.png" />

#### Frappé

<img src="./images/CatppuccinFrappe.png" />

#### Macchiato

<img src="./images/CatppuccinMacchiato.png" />

#### Mocha

<img src="./images/CatppuccinMocha.png" />

---

## 背景

既存の Catppuccin for Visual Studio テーマは、
Visual Studio 2026 への対応が進行中であり、
現時点では正式対応版が利用できませんでした。

そのため、

- 自身の開発環境で利用するため
- Visual Studio 2026 のテーマ拡張機能仕様を理解するため

という目的で、本テーマを作成しています。

本リポジトリは非公式の派生プロジェクトであり、
公式 Catppuccin プロジェクトとは直接の関係はありません。

---

## 特徴

- Catppuccin のカラーパレットをベースにした配色
- Visual Studio 2026 の新しいテーマ定義方式に対応
- Editor / Text / 基本 UI トークンを中心に定義
- 未定義の UI 要素は Visual Studio 標準テーマへフォールバック
- 個人利用を想定したシンプルな構成

---

## 対応環境

- Visual Studio 2026
- Windows 10 / Windows 11

---

## インストール方法

### 方法1: VSIX ファイルから手動インストール

1. GitHub Releases から `.vsix` ファイルをダウンロード
2. ダブルクリックしてインストール
3. Visual Studio を再起動
4.  
   `ツール` → `オプション` → `環境` → `全般` → `配色テーマ`  
   から本テーマを選択

### 方法2: ソースコードからビルド（開発者向け）

```bash
git clone https://github.com/sysCat64/CatppuccinModernForVisualStudio.git
