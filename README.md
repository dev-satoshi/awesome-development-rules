<h1>Development Rules</h1>

<h2>目次</h2>

- [コーディングスタイル](#code-style)
- [レビュー](#review)
- [テスト](#test)
- [ドキュメントの整備](#document)
- [Gitの運用について](#git-operation)
- [CSS設計](#css-design)
- [コンポーネント設計]()
- [便利なテンプレート](#template)



<h2 id="code-style">コーディングスタイル</h2>
チーム内で合意したコーディング規約、スタイルガイド、原則を遵守する。<br>
コードは明確で読みやすく、コメントを適切に付ける。


<h2 id="review">レビュー</h2>
新しい機能やバグ修正のたびに、他のメンバーにコードレビューを依頼する。


<h2 id="test">テスト</h2>
新しい機能を追加した際や、既存の機能を修正した際には、関連するテストを必ず記述する。<br>
すべてのテストがパスしてからマージを行う。<br>


<h2 id="document">ドキュメントの整備</h2>
開発に関するドキュメントや設計書は適宜更新し、最新の状態を維持する。

<h4>READMEに記載すること</h3>

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
<h3>ブランチ戦略</h3>
<h4>Git-flow</h4>

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| develop | 開発中のものを置くブランチ |
| release | 次にリリースするものを置くブランチ |
| feature/* | 新機能開発や不具合の修正に使うブランチ |
| hotfix/* | 公開中のもののバグ修正用ブランチ |
| sandbox | なんでも |

<h4>GitHub-flow</h4>

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| feature/* | 作業用ブランチ |

<h4>※branch運用基本ルール</h4>
mainに直push禁止<br>
原則1ブランチ1機能<br>
作業はfeatureブランチから分岐させる<br>
作業ブランチはマージ後に削除<br>
できるだけレビューする(誰かにしてもらう)<br>

<h3>Issue & PullRequest</h3>
タスクやバグ、機能の追加など、具体的な作業内容はIssueに記述し、それに基づいて作業を行う。<br>
作業が完了したら、Pull Requestを作成し、他のメンバーにレビューを依頼する。<br>

<h3>Commit Message</h3>
コミットメッセージはPrefixを使い、明確に変更内容を伝えるものとする。

<h4>Prefix（コミットメッセージ記法）</h4>

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

<h4>※コミットメッセージの例</h4>

- init
- chore: Reactと依存関係を追加
- add: ユーザー登録機能を追加
- sleep: I'm so sleepy

<h4>Prefix(短縮Ver)</h4>

| Prefix | 説明 |
| --- | --- |
| add | 追加(ファイル、機能) |
| remove, delete | 削除(ファイル、機能) |
| update | 機能修正(バグではない) |
| fix | バグ修正 |


<h2 id="css-design">CSS設計</h3>

- BEM
- OOCSS


<h2 id="template">便利なテンプレート</h3>

- [PullRequest](https://gist.github.com/dev-satoshi/65a0ac8b772b83c1ce73f4f460acd45e)
- [ユーザーストーリー](https://gist.github.com/dev-satoshi/569f44c5a074c9e1cb09269e717f8327)
- [デイリースクラム](https://gist.github.com/dev-satoshi/f2bf3571666482fe37ec9c8d30c7451c)



