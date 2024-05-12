<h1>Awesome Development Rules</h1>

`Awesome Development Rules`は、ソフトウェア開発のベストプラクティスとガイドラインをまとめた、包括的で実践的なリポジトリです。<br>
このリポジトリは、開発者、チーム、組織が、より高品質、保守性、スケーラブルなソフトウェアを開発するための指針を提供することを目的としています。


<h1>目次</h1>

- [コーディングスタイル](#code-style)
- [パッケージ原則](#package-principles)
- [コーディング原則](#code-principle)
- [レビュー](#review)
- [テスト](#test)
- [ドキュメントの整備](#document)
- [Gitの運用について](#git-operation)
- [リリース制御（Feature Flag）](#release-control)
- [チームビルディング](#team-building)
- [リファレンス](#reference)
- [便利なテンプレート](#template)
- [お得な情報](#deals)
<!-- - [CSS設計](#css-design) -->


<h1 id="code-style">コーディングスタイル</h1>
チーム内で合意したコーディング規約、スタイルガイド、原則を遵守する。<br>
コードは明確で読みやすく、コメントを適切に付ける。

<h2>ドキュメンテーションコメントを使う</h2>
ドキュメンテーションコメント（Documentation Comments）は、ソースコード内に挿入される特殊なコメントで、ソフトウェアの要素（関数、クラス、モジュールなど）に対するドキュメンテーションや説明を提供するためのものです。

#### Pythonの場合（Docstring）

```
def count_characters(text: str) -> int:
  """文字列の長さを返します。

  この関数は、与えられた文字列の長さを計算し、その値を返します。

  Args:
      text: 文字列。

  Returns:
      int: 文字列の長さ。

  Raises:
      TypeError: 引数が文字列ではない場合。

  Examples:
      >>> count_characters("Hello world!")
      12

  Note:
      空文字列("")の場合、0を返します。
  """

  if not isinstance(text, str):
    raise TypeError("引数は文字列である必要があります。")

  return len(text)
```

#### JSの場合（JSDoc）

```
/**
 * これはJSDocコメントです。この関数に対するドキュメンテーションを提供します。
 *
 * @param {string} parameter パラメータの説明。
 * @returns {number} 戻り値の説明。
 */
function exampleFunction(parameter) {
  // 関数の実装
  return parameter.length;
}
```

#### TSの場合（TSDoc）

```
/**
 * これはTSDocコメントです。この関数に対するドキュメンテーションを提供します。
 *
 * @param parameter パラメータの説明。型は`string`です。
 * @returns 戻り値の説明。型は`number`です。
 */
function exampleFunction(parameter: string): number {
  // 関数の実装
  return parameter.length;
}
```

<h2>アノテーションコメントでわかりやすくコメントを残す</h3>

#### Betterコメント

```
// * 強調
// ! 警告
// ? 疑問
// TODO: タスク
// FIXME: 不具合がある
// HACK: あまり綺麗じゃない解決策
// XXX: 大きな問題がある
```

#### アノテーションコメントを一覧で見ることができるVSCode拡張機能
[Todo Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)

<h2>Twelve-Factor App</h2>
モダンなWebアプリケーションとしてあるべき姿を12のベストプラクティスにまとめた方法論です。<br>
この方法論は、以下の12の要素から成り立っています。

1. コードベース<br>
バージョン管理されている1つのコードベースと複数のデプロイ
2. 依存関係<br>
依存関係を明示的に宣言し分離する
3. 設定<br>
設定を環境変数に格納する
4. バックエンドサービス<br>
バックエンドサービスをアタッチされたリソースとして扱う
5. ビルド、リリース、実行<br>
ビルド、リリース、実行の3つのステージを厳密に分離する
6. プロセス<br>
アプリケーションを1つもしくは複数のステートレスなプロセスとして実行する
7. ポートバインディング<br>
ポートバインディングを通してサービスを公開する
8. 並行性<br>
プロセスモデルによってスケールアウトする
9. 廃棄容易性<br>
高速な起動とグレースフルシャットダウンで堅牢性を最大化する
10. 開発/本番一致<br>
開発、ステージング、本番環境をできるだけ一致させた状態を保つ
11. ログ<br>
ログをイベントストリームとして扱う
12. 管理プロセス<br>
管理タスクを1回限りのプロセスとして実行する


<h1 id="package-principles">パッケージ原則</h1>
パッケージ原則とは、ソフトウェア開発におけるパッケージ設計の指針となる6つの原則です。<br>
これらの原則は、パッケージを再利用可能で保守しやすいものにするために役立ちます。

<h2>再利用・リリース等価の原則</h2>
リリースされたものだけを再利用するか、再利用するならばそれをリリースするという考え方です。<br>
つまり、パッケージ内のクラスは、全て再利用可能か、全て再利用不可能かのいずれかにする必要があります。<br>
中途半端にリリースされた状態ではなく、完全にリリースされた状態でなければなりません。<br>
中途半端な状態でリリースされたものを使用すると、自分のコードが予期せぬ書き換えを受ける可能性があります。<br>

<h2>全再利用の原則</h2>
一度リリースされたパッケージに起きたコード変更は、全て利用するか、全く利用しないかの二者択一を強調します。<br>
利用者は必要な変更と不要な変更を選択する権限を持たず、パッケージのバージョンアップなどで欲しい機能と都合の悪い機能が一緒に含まれると、ユーザーは新旧バージョンから選択するしかありません。<br>
このような問題は、パッケージに含まれる機能が多すぎることが原因で、適切に分割されていれば必要なパッケージだけを交換でき、影響範囲が小さいため副作用の心配も軽減されます。<br>
アプリケーションの開発においては、共通の機能を持つクラスは同じパッケージにまとめ、パッケージ内のクラスは関連性が高く、凝集度が高いものでなければなりません。

<h2>閉鎖性共通の原則</h2>
ソフトウェアのパッケージ内に含まれるクラスが同じ種類の変更に対して閉じているべきであることを強調します。<br>
つまり、1つの変更が必要な際、できる限り1つのパッケージだけを交換することを目指す原則です。<br>
パッケージが閉じているとは、そのパッケージ内の責務が自己完結していることを意味します。<br>
よくあるのが、共通的なクラスをたくさん詰め込んだCommonパッケージです。<br>
全てのクラスがCommonパッケージを参照してしまい、影響範囲が予測できなくなります。<br>
関連性の高いクラスは同じパッケージにまとめるべきであり、異なる理由で修正されるクラスは別のパッケージに分けるべきです。<br>
これにより、影響範囲が予測可能であり、保守性が向上します。<br>

<h2>非循環依存関係の原則</h2>
パッケージの依存が循環してはならないというシンプルな原則。<br>
循環依存とは、パッケージAを使うにはパッケージBが必要で、パッケージBを使うにはパッケージAが必要と、依存関係がぐるぐる回ってしまう状態のことです。<br>
循環依存が発生すると、デバッグが困難になる（問題が発生した場合、原因となるパッケージを特定するのが困難になる）、リリースが困難になる（あるパッケージを変更すると、循環している他のパッケージにも変更が必要になり、リリースが複雑になる）、テストが困難になる（循環しているパッケージ同士をテストするのが困難になる）といった問題が出てきます。<br>
また、クラス単体ならわかりやすいのですが、パッケージになると、パッケージAに使われるパッケージBがパッケージCを使ったところ、実はパッケージCがパッケージAを使っていたという、気づきにくい循環依存が出来上がってしまいます。<br>
したがって、パッケージ設計をするときは、必ず片方向の依存関係にする。または、強い関係はパッケージ内で閉じるようにする。<br>

<h2>安定依存の原則</h2>
パッケージの依存は常により安定したパッケージに向くべきであるという原則。<br>
変更の少ない安定したパッケージに対して依存するようにすることで、変更の影響を最小限に抑えることができます。<br>
ここで大事なのは、安定したパッケージに向けるべきではなく、常に向くことが重要です。<br>
ここでいう安定とは、変更しづらいという意味です。<br>
不安定に依存するとそれ以上の安定はないです。<br>

<h2>安定度・抽象度等価の原則</h2>
パッケージの抽象度と安定度は同程度でなければならないという原則。<br>
つまり、安定度の高いパッケージは抽象的でなければならず、逆に安定度の低いパッケージで良い場合は、抽象度が低い（具体的）で良いと言ってます。<br>


<h1 id="code-principle">コーディング原則</h1>
<h2>SOLID</h2>
SOLID原則は、オブジェクト指向プログラミングのコーディング慣例として広く採用される、5つの基本的な原則を表します。<br>
これらの原則は、ソフトウェアをより理解しやすく、より柔軟に、よりメンテナナンス性の高いものにすることを目的としています。<br>

#### 単一責任の原則（Single Responsibility Principle）<br>
1つのモジュール（データや関数をまとめた凝集性のあるもの）は1つだけの責務を負うべき。<br>
モジュールが1つの責務だけを持つことで、変更が発生した際に影響範囲を最小限に抑えることができる。<br>
#### 解放閉鎖の原則（Open Closed Principle）<br>
ソフトウェアの構成要素（クラス、関数、モジュール等）は拡張に対して開き、修正に対して閉じていなければならない。<br>
既存のコードを変更せずに新しい機能を追加（拡張）できるようにすることで、柔軟性、再利用性、保守性を確保する。<br>
#### リスコフの置換原則（Liskov Substitution Principle）<br>
基本型（親クラス）はその派生型（子クラス）で置換可能であるべき。<br>
派生型が基本型として振る舞えることで、コードの予測可能性と拡張性を確保する。<br>
#### インターフェースの分離の原則（Interface Segregation Principle）<br>
クライアントは使わないインタフェースの実装を強制されるべきではない。<br>
インタフェースを小さい単位に分離することで、各クライアントは実際に自分が利用するメソッドだけに依存するようになり、他のクライアントの変更の影響を最小限に抑えることができる。<br>
#### 依存性逆転の原則（Dependency Inversion Principle）<br>
上位のモジュール（上位の機能）は下位のモジュール（下位の機能）に依存してはならない。どちらのモジュール（機能）も抽象に依存すべきである。<br>
抽象は実装の詳細に依存してはならない。実装の詳細が抽象に依存すべきである。<br>
モジュールが具体的な実装に依存していないため、異なるコンテキストでも再利用しやすくなります。<br>

<h2>KISS（Keep It Simple, Stupid）</h2>
目的：シンプルなソリューションが複雑なものよりも優れているという考え方。<br>
理由：冗長なコードや複雑な構造はバグの原因となりやすく保守性が低下する。<br>

<h2>DRY（Don’t Repeat Yourself）</h2>
目的：同じコードやロジックを重複せずに再利用すること。<br>
理由：共通の機能やロジックを関数やクラスにまとめることで、変更が発生した場合に一箇所の修正で済み、コードの一貫性が保たれる。<br>

<h2>YAGNI（You Ain’t Gonna Need It）</h2>
目的：将来の利用を想定せず、不必要な機能や拡張を避けて開発効率を向上させる。<br>
理由：不必要な機能は開発時間の無駄であり、過剰な拡張はコードベースを複雑にし、保守性を低下させるから。<br>

<h2>SLAP（Single Level of Abstraction Principle）</h2>
目的：コード内で同じレベルの抽象度を維持すること。<br>
理由：コードの読みやすさを向上させ、理解が容易になり、保守性が向上する。<br>

<h2>Separation of Concerns</h2>
目的：システムを異なる概念や機能に基づいて複数の独立した部分に分割すること。<br>
理由：関心ごとの分離により、モジュール性が向上し、変更が特定の領域に制限され、保守性と拡張性が向上する。<br>

<h2>Leaky Abstraction</h2>
目的：抽象化が完全でなく、内部の実装の詳細が漏れることを最小限に抑えること。<br>
理由：完全な抽象化が難しい場合、詳細が漏れると、使用者が予測できない挙動や問題に直面する可能性があるため。<br>


<h1 id="review">レビュー</h1>
コードレビューは、作成者とは異なる視点でコードをチャックすることにより、本人では気付きにくいバグ（ミス、問題点）を発見しやすく、プログラムの品質向上に役立ちます。<br>
また、レビュアー（レビューされる人）とレビュイー（レビューする人）が、お互いコードについて意見交換をすることで、技術知識を共有することができます。<br>
さらに、共通の評価基準（ガイドライン）を作成することで、一貫した品質を保つことができます。<br>

## レビューガイドライン
| 観点 | 概要	| 詳細 |
| --- | --- | --- |
| Design | アーキテクチャ、設計、設計原則 | アプリケーションとして一貫性のあるアーキテクチャ、設計になっているか。アプリケーションにとって適切な責務、振る舞いになっているか。
| Functionality	| 機能（要件）を満たしているか | 作者の意図通りに動作するか。システムの通信量、パフォーマンスに懸念がないか。 |
| Simplicity | 理解容易性 | 可読性のあるコーディングになっているか。処理ができるだけシンプルな振る舞いになっているか。 |
| Test | テストの記述、パターンが適切 | システムとして適切な自動テストを兼ね備えているか。自動テストの内容で品質を担保できているか。 |
| Naming | クラス、メソッド、変数名などの命名 | 変数やクラス、メソッドに責務を意図した明確な名前が付けられているか。英語文法に誤りがないか。typoもこれに含まれる。 |
| Style	| コードスタイル | コードスタイルが言語仕様に準拠しているか。 |
| Comment | コメント | コメントは明確で有益化か。ドキュメンテーションコメント、アノテーションコメントが適切な内容であるか。 |
| Document | ドキュメント | 関連するドキュメントは更新されているか。その内容は適切か。 |

[Google's Engineering Practices documentationを参考にしています。](https://fujiharuka.github.io/google-eng-practices-ja/ja/review/)

## 修正要否ガイドライン
| 観点 | 詳細 |
| --- | --- |
| MUST | 必ず対応してほしいこと。 |
| SHOULD | 細かい指摘や気になること。 |
| IMO | レビュアー個人の意見。 |
| Q | 不明瞭で質問したいこと。 |

## コードレビューでの指摘方法
レビューガイドラインの7つの観点に加えて、修正要否ガイドラインの観点4つをPrefixに組み合わせ、コメントします。

#### コードレビューの例
MUST(Design)：◯◯クラスの責務が複数あり、単一責任の原則に反している。


<h1 id="test">テスト</h1>
新しい機能を追加した際や、既存の機能を修正した際には、関連するテストを必ず記述する。<br>
すべてのテストがパスしてからマージを行う。<br>


<h1 id="document">ドキュメントの整備</h1>
開発に関するドキュメントや設計書は適宜更新し、最新の状態を維持する。


<h1 id="git-operation">Gitの運用について</h1>
<h2>ブランチ戦略</h2>

### Git-flow
長期的な開発とリリースの管理を目的としたブランチ戦略

| branch | 説明 |
| --- | --- |
| main | 本番環境 |
| develop | 開発中のものを置くブランチ |
| release | 次にリリースするものを置くブランチ |
| feature/* | 新機能開発や不具合の修正に使うブランチ |
| hotfix/* | 公開中のもののバグ修正用ブランチ |

### GitHub-flow
シンプルで柔軟なブランチ戦略

| branch | 説明 |
| --- | --- |
| main | 本番環境 |
| feature/* | 作業用ブランチ |

### GitLab-flow
Git-flowとGitHub-flowを組み合わせたブランチ戦略

### トランクベース開発
頻繁なアップデートをmainブランチ(トランク)での直接の開発を促進し、継続的かつ頻繁な統合を重視する戦略

<h2>branch運用基本ルール</h2>
mainに直push禁止<br>
原則1ブランチ1機能<br>
作業はfeatureブランチから分岐させる<br>
作業ブランチはマージ後に削除<br>
できるだけレビューする(誰かにしてもらう)<br>

<h2>Issue & PullRequest</h2>
タスクやバグ、機能の追加など、具体的な作業内容はIssueに記述し、それに基づいて作業を行う。<br>
作業が完了したら、Pull Requestを作成し、他のメンバーにレビューを依頼する。<br>

<h2>Commit Message</h2>
コミットメッセージはPrefixを使い、明確に変更内容を伝えるものとする。

### Prefix（コミットメッセージ記法）

| Prefix | 説明 |
| --- | --- |
| init | first commit |
| chore | ビルドプロセスやドキュメント生成などの補助ライブラリの変更 |
| add | 追加(ファイル、機能) |
| feat, feature | 追加(機能、ファイル) |
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

### Prefix(短縮Ver)

| Prefix | 説明 |
| --- | --- |
| add | 追加(ファイル、機能) |
| remove, delete | 削除(ファイル、機能) |
| update | 機能修正(バグではない) |
| fix | バグ修正 |

#### コミットメッセージの例

- init
- chore: Reactと依存関係を追加
- add: ユーザー登録機能を追加
- sleep: I'm so sleepy


<h2 id="release-control">リリース制御（Feature Flag）</h2>
ソフトウェア開発におけるシステムの挙動（機能）のオン・オフをコードの変更なしで動的に切り替えられる仕組みです。
Feature Flagを活用することで、開発効率の向上、リスクの低減、ユーザー満足度の向上を実現できます。

※Feature Flagとは別に[Future Flag](https://remix.run/blog/future-flags)というものもある


#### 新機能の段階的なリリース
- 開発中の機能を一部のユーザーに先行公開し、テストやフィードバックを得ながら段階的にリリース
- ユーザーごとに機能のオン・オフを切り替えることで、A/Bテストや多人数テストを実施

#### 機能の迅速なロールバック
- 問題が発生した場合、コードの変更を待たずに機能を迅速に無効化
- ロールバックによる影響範囲を最小限に抑え、ユーザーへの影響を軽減

#### リスクの高い変更の安全な導入
- 本番環境にデプロイ後、ユーザーへの影響を確認してから機能を有効化
- 不具合が発生した場合でも、コードの変更なしで迅速にロールバック

#### 具体的な利用例
- 新しいデザインのUIを特定のユーザーに先行公開
- 有料プランの機能を無料プランユーザーに一時的に開放
- 地域やデバイスごとに機能の表示を制御
- バグ修正中の機能を一時的に無効化

#### サンプルコード
```
export const Page = () => {
  if (featureFlag) {
    return <NewFeature />
  } else {
    return <CurrentFeature />
  }
}
```


<!--
<h1 id="css-design">CSS設計</h1>

- BEM
- OOCSS
-->

<h1 id="team-building">チームビルディング</h1>
<h2>チームの最適人数(二枚のピザルール)</h2>
「二枚のピザルール」は、AmazonのCEOであるジェフ・ベゾスが提唱した考え方で、仕事のチームの人数はピザ2枚で賄える4人〜8人程度が最も望ましいとされています。このルールの目的は、会議の生産性を高めることです。
具体的には、会議の参加者が多いほど、生産性は低下すると考えられています。これを解決するために、参加メンバーを2枚のピザを分け合える人数に抑えるのです。大勢が会議に参加すれば、創造性が犠牲になるという考え方が背景にあります。

#### ルールの詳細
会議の参加者が多いほど、生産性は低下すると考えられています。これを解決するために、参加メンバーを2枚のピザを分け合える人数に抑えるのです。大勢が会議に参加すれば、創造性が犠牲になるという考え方が背景にあります。

#### ルールの適用
しかし、このルールを単純に利用するだけでは意味がないと指摘されています。大企業の場合、チーム1つ1つは小規模であっても、自律性や生産性が失われる可能性があります。そのため、このルールを適用する際には、チームの自律性やミッションを考慮することが重要とされています。

#### 会議の工夫
また、会議の進行役を任命したり、基本的なルールを設けたり、議題が参加者全員と関係あるかを事前に確認するなどの工夫が必要とされています。このように、「二枚のピザルール」は、会議の効率性と生産性を向上させるための一つの戦略と言えます。

<h2>質問する適切なタイミング(Google人工知能チームの15分ルール)</h2>
Googleの人工知能チームが採用している「15分ルール」は、問題解決のための効率的なアプローチを提供します。

#### ルールの詳細
1. 最初の15分は自分で解決を試みます。
2. 15分経っても解決できない場合は、必ず他の人に聞きます。

#### ルールの目的
このルールの目的は、時間の最適な利用と効率的な問題解決を促進することです。
前者のステップを守らないと他人の時間を無駄にし、後者のステップを守らないと自分の時間を無駄にするとされています。

#### ルールの適用
このルールはあくまで一つの指標であり、個々の状況により適切な時間やルールを決めることが重要です。


<h2>質問の方法</h2>
質問をする際は、自分が試したことや調べた内容を明示することで、質問を受ける側が解決策を見つけやすくなります。

### 質問する際の注意点
#### 質問する
1. 最も適切なチャネルで質問するようにしてください。同じメッセージを複数のチャネルに投稿しないでください。
2. 質問してもよいかどうかを尋ねるのではなく、ただ質問してください。できるだけ詳細を含めてください。
3. 質問する前によく調べてください。ドキュメントを検索し、検索エンジンを使用し、時間をかけて自分で答えを見つけるのは素晴らしい学習方法です。
4. 質問の回答に時間がかかる場合は、スレッドを作成してください。これは、他の人が混乱したり、チャネル内を何度もスクロールしたりすることなく、同時に質問できることを意味します。同様に、質問に質問で答える場合は、スレッドを作成してください。
5. あなたを助けるために費やした人々の時間を尊重してください。
6. たとえ以前にあなたを助けてくれたことがあるとしても、助けを求める人に DM を送らないでください。サーバー内でのみ質問することで、誰もが利益を得ることができます。

#### コードを共有する
コードを共有する必要がある場合がよくあります。これを行うには主に2つの方法があります。
1. コードの記述量が少ない場合は、マークダウン構文を使用する。
2. コードの記述量が多い場合は、GitHubのリポジトリやGistのリンクを共有する。

#### ※コードや端末出力の画像を投稿しない
コードの画像を投稿すると、読みにくいし、文字のコピーなどができないため、ヘルプを提供するのが難しくなる。
スクリーンショットは、ブラウザでの出力の問題を示す目的でのみ使用してください。

#### 質問する際のコツ(PREP法)
PREP法とは、Point(ポイント)、Reason(理由)、Example(例)、Point(ポイント)の頭文字を取ったもので、意見やアイデアを効果的に伝えるためのコミュニケーション手法です。具体的な手順は以下の通りです。

1. Point(ポイント)：最初に主張や結論を述べます。これはあなたが何を伝えたいのかを明確にするためのものです。
2. Reason(理由)：次に、その主張や結論を支持する理由を述べます。これはあなたの主張が信頼できるものであることを示すためのものです。
3. Example(例)：その後、具体的な例やエビデンスを提供します。これはあなたの理由が具体的で実際的なものであることを示すためのものです。
4. Point(再度ポイント)：最後に、最初の主張や結論を再度述べます。これはあなたのメッセージを強調し、リスナーにそれを覚えてもらうためのものです。


<h1 id="reference">リファレンス</h1>

- [Google Styleguide](https://github.com/google/styleguide/tree/gh-pages)
- [Twelve-Factor App](https://12factor.net/ja/)


<h1 id="template">便利なテンプレート</h1>

- [質問](https://gist.github.com/dev-satoshi/4357a9d270b50c78ad9dd45e8c78ec7f)
- [README](https://gist.github.com/dev-satoshi/e362c790eb5f6b64e35ed5db6155ea1d)
- [Feature Request](https://gist.github.com/dev-satoshi/95bc731b41660a2167d55e7a961a8fdc)
- [Bug Report](https://gist.github.com/dev-satoshi/db76940bdd018ca42be8c08c60bc1fa4)
- [Pull Request](https://gist.github.com/dev-satoshi/65a0ac8b772b83c1ce73f4f460acd45e)
- [ゴールデンサークル理論](https://gist.github.com/dev-satoshi/523ca18d0099f02ba293c412f7d1d8e5)
- [ユーザーストーリー](https://gist.github.com/dev-satoshi/255f96a59562a7b613dfb1aa6ad0beca)
- [デイリースクラム](https://gist.github.com/dev-satoshi/f2bf3571666482fe37ec9c8d30c7451c)
- [記事の構成](https://gist.github.com/dev-satoshi/75db364f8af8eb7a903617c3ed5d720a)
- [ユビキタス言語](https://gist.github.com/dev-satoshi/31eb5769391063a7ccce8c9c51fd8034)


<h1 id="deals">お得な情報</h1>

- [ホスティングサービス](https://gist.github.com/dev-satoshi/da065ccd2e8a872020ab9734fc90ee27)
