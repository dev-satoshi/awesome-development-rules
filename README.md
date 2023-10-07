<h1>Development Rules</h1>

<h2>目次</h2>

- [READMEに記載すること](#readme)
- [Gitの運用について](#git-operation)
- [CSS設計](#css-design)

- [コンポーネント設計]()

<h2 id="readme">READMEに記載すること</h2>

- プロジェクトの概要
- 目次
- 使用技術(Sheid, Simple Iconsを使用)
- システム構成
- ER図
- ディレクトリ構成
- 必要な環境変数やコマンド一覧
- 開発環境の構築方法
- 作業する上で参考になりそうな記事一覧

<h2 id="git-operation">Gitの運用について</h2>

<h3>branch命名ルール</h3>

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| develop | 開発中のものを置くブランチ |
| release | 次にリリースするものを置くブランチ |
| feature/* | 新機能開発に使うブランチ |
| hotfix/* | 公開中のもののバグ修正用ブランチ |
| sandbox | なんでも |

※ branch運用基本ルール
- mainに直push禁止
- 原則1ブランチ1機能
- 作業はfeatureブランチから分岐させる
- 作業ブランチはマージ後に削除
- できるだけレビューする(誰かにしてもらう)

<h3>Prefix（コミットメッセージ記法）</h3>

| Prefix | 説明 |
| --- | --- |
| init | first commit |
| chore | ビルドプロセスやドキュメント生成などの補助ライブラリの変更 |
| add | 追加(ファイル、機能) |
| update | 機能修正(バグではない) |
| perf | パフォーマンスを向上させるためのコード変更 |
| refactor | 整理(リファクタリング等) |
| change | 仕様変更 |
| fix | バグ修正 |
| remove, delete | 削除(ファイル、機能) |
| revert | 変更取り消し |
| test | 不足しているテストの追加や既存のテストの修正 |
| docs | ドキュメンテーションのみの変更 |
| merge | ブランチをマージ |
| sleep | 寝たw |

※ コミットメッセージの例
- init
- chore: Reactと依存関係を追加
- add: ユーザー登録機能を追加
- sleep: I'm so sleepy

<h3>Prefix(短縮Ver)</h3>

| Prefix | 説明 |
| --- | --- |
| add | 追加(ファイル、機能) |
| remove | 削除(ファイル、機能) |
| update | 機能修正(バグではない) |
| fix | バグ修正 |

<h3 id="css-design">CSS設計</h3>

- BEM
