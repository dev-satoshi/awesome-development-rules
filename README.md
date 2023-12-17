<h1>Awesome Development Rules</h1>

<h2>目次</h2>

- [コーディングスタイル](#code-style)
- [コーディング原則](#code-principle)
- [レビュー](#review)
- [テスト](#test)
- [ドキュメントの整備](#document)
- [Gitの運用について](#git-operation)
- [CSS設計](#css-design)
- [コンポーネント設計]()
- [リファレンス](#reference)
- [便利なテンプレート](#template)



<h2 id="code-style">コーディングスタイル</h2>
チーム内で合意したコーディング規約、スタイルガイド、原則を遵守する。<br>
コードは明確で読みやすく、コメントを適切に付ける。

<h3>DocstringやJSDocなどを使いコメントを残す</h3>

<h3>Betterコメントでわかりやすくコメントを残す</h3>

- // ! 警告
- // ? 疑問
- // * 強調
- // TODO タスク

<h2 id="code-principle">コーディング原則</h2>
<h3>SOLID</h3>
SOLID原則は、オブジェクト指向設計の5つの基本的な原則を表します。<br>
これらの原則は、ソフトウェアの保守性と拡張性を向上させることを目的としています。<br>

- 単一責任の原則（Single Responsibility）<br>
目的：1つのクラスは1つの責任を持つべき。<br>
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

<h3>KISS（Keep It Simple, Stupid）</h3>
目的：シンプルなソリューションが複雑なものよりも優れているという考え方。<br>
理由：冗長なコードや複雑な構造はバグの原因となりやすく保守性が低下する。<br>

<h3>DRY（Don’t Repeat Yourself）</h3>
目的：同じコードやロジックを重複せずに再利用すること。<br>
理由：共通の機能やロジックを関数やクラスにまとめることで、変更が発生した場合に一箇所の修正で済み、コードの一貫性が保たれる。<br>

<h3>YAGNI（You Ain’t Gonna Need It）</h3>
目的：将来の利用を想定せず、不必要な機能や拡張を避けて開発効率を向上させる。<br>
理由：不必要な機能は開発時間の無駄であり、過剰な拡張はコードベースを複雑にし、保守性を低下させるから。<br>

<h3>SLAP（Single Level of Abstraction Principle）</h3>
目的：コード内で同じレベルの抽象度を維持すること。<br>
理由：コードの読みやすさを向上させ、理解が容易になり、保守性が向上する。<br>

<h3>Separation of Concerns</h3>
目的：システムを異なる概念や機能に基づいて複数の独立した部分に分割すること。<br>
理由：関心ごとの分離により、モジュール性が向上し、変更が特定の領域に制限され、保守性と拡張性が向上する。<br>

<h3>Leaky Abstraction</h3>
目的：抽象化が完全でなく、内部の実装の詳細が漏れることを最小限に抑えること。<br>
理由：完全な抽象化が難しい場合、詳細が漏れると、使用者が予測できない挙動や問題に直面する可能性があるため。<br>


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


<h2 id="css-design">CSS設計</h2>

- BEM
- OOCSS


<h2 id="reference">リファレンス</h2>

- [Google Styleguide](https://github.com/google/styleguide/tree/gh-pages)


<h2 id="template">便利なテンプレート</h2>

- [質問](https://gist.github.com/dev-satoshi/4357a9d270b50c78ad9dd45e8c78ec7f)
- [Pull Request](https://gist.github.com/dev-satoshi/65a0ac8b772b83c1ce73f4f460acd45e)
- [ユーザーストーリー](https://gist.github.com/dev-satoshi/255f96a59562a7b613dfb1aa6ad0beca)
- [デイリースクラム](https://gist.github.com/dev-satoshi/f2bf3571666482fe37ec9c8d30c7451c)


