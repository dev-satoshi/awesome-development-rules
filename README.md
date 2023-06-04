## 目次
- [システム構成について](#system-configuration)
- [各種リポジトリのリンク](#repository)
- [使用技術について](#technology-used)
- [環境構築]()
- [ディレクトリ設計]()
- [コンポーネント設計]()
- [基本的な作業手順]()
- [コンポーネント設計]()
- [Gitの運用について]()
- [作業する上で参考になりそうな記事一覧]()

<h2 id="system-configuration">開発構成の概要</h2>
<h2 id="repository">各種リポジトリのリンク</h2>
<h2 id="technology-used">使用技術について</h2>

<h1 id="git-operation">Gitの運用について</h1>

<h3 id="branch">branch命名ルール</h3>

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| develop | 開発中のものを置くブランチ |
| release | 次にリリースするものを置くブランチ |
| feature-/* | 新機能開発中に使うブランチ |
| hotfix-/* | 公開中のもののバグ修正用ブランチ |
| sandbox | なんでも |

※ branch運用基本ルール
- mainに直push禁止
- 作業はfeatureブランチから分岐させる
- 作業ブランチはマージ後に削除
- できるだけレビューする(誰かにしてもらう)

<h3 id="prefix">Prefix（コミットメッセージ記法）</h3>

| Prefix | 説明 |
| --- | --- |
| init | first commit |
| setup | プロジェクトのセットアップ(プロジェクトに必要なパッケージの追加) |
| add | 新規（ファイル、機能） |
| update | 機能修正(バグではない) |
| perf | パフォーマンスを向上させるためのコード変更 |
| refactor | 整理(リファクタリング等) |
| change | 仕様変更 |
| fix | バグ修正 |
| remove | 削除(ファイル、機能) |
| revert | 変更取り消し |
| test | 不足しているテストの追加や既存のテストの修正 |
| docs | ドキュメンテーションのみの変更 |
| chore | ビルドプロセスやドキュメント生成などの補助ライブラリの変更 |
| merge | ブランチをマージ |
| sleep | 寝たw |

※ コミットメッセージの例
- init
- setup: プロジェクトのセットアップ
- add: ユーザー登録機能の追加
- sleep: I'm so sleepy
