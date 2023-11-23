<h1>Development Rules</h1>

<h2>目次</h2>

- [コーディングスタイル](#code-style)
- [コーディング原則](#code-principle)
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


<h2 id="code-principle">コーディング原則</h2>
<h3>SOLID原則</h3>

- 単一責任の原則（Single Responsibility）<br>
目的：1つのクラスは1つの責任を持つべき<br>
理由：クラスが1つの責務だけを持つことで、変更が発生した際に影響範囲を最小限に抑える。<br>
- オープン/クローズドの原則（Open/Closed Principle）<br>
目的：クラスは拡張に対して開き、修正に対して閉じていなければならない。<br>
理由：既存のコードを変更せずに新しい機能を追加できるようにすることで、柔軟性、拡張性、安定性を確保する。<br>
- リスコフの置換原則（Liskov Substitution Principle）<br>
目的：基本型(親クラス)はその派生型(子クラス)で置換可能であるべき。<br>
理由：派生型が基本型として振る舞えることで、コードの予測可能性と拡張性を確保する。<br>
- インターフェースの分離の原則（Interface Segregation Principle）<br>
目的：クライアントが利用しないメソッドに依存すべきではない。<br>
理由：クライアントが利用しないメソッドに依存しないことで、冗長な依存関係を回避する。<br>
- 依存性逆転の原則（Dependency Inversion Principle）<br>
目的：高水準のモジュール(上位の機能)は低水準のモジュール(下位の機能)に依存すべきではなく、どちらも抽象に依存すべき。<br>
理由：高水準のモジュールが低水準のモジュールに依存せず、抽象に依存することで、柔軟性と拡張性を向上させる。<br>


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
長期的な開発とリリースの管理を目的としたブランチ戦略

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| develop | 開発中のものを置くブランチ |
| release | 次にリリースするものを置くブランチ |
| feature/* | 新機能開発や不具合の修正に使うブランチ |
| hotfix/* | 公開中のもののバグ修正用ブランチ |
| sandbox | なんでも |

<h4>GitHub-flow</h4>
シンプルで柔軟なブランチ戦略

| branch | 説明 |
| --- | --- |
| main | 本番環境 | 
| feature/* | 作業用ブランチ |

<h4>GitLab-flow</h4>
Git-flowとGitHub-flowを組み合わせたブランチ戦略

<h4>トランクベース開発</h4>
頻繁なアップデートをmainブランチ(トランク)での直接の開発を促進し、継続的かつ頻繁な統合を重視する戦略

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

- [Pull Request](https://gist.github.com/dev-satoshi/65a0ac8b772b83c1ce73f4f460acd45e)
- [ユーザーストーリー](https://gist.github.com/dev-satoshi/569f44c5a074c9e1cb09269e717f8327)
- [デイリースクラム](https://gist.github.com/dev-satoshi/f2bf3571666482fe37ec9c8d30c7451c)

