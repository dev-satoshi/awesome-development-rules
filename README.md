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

## Gitの運用について
<h2 id="branch">ブランチについて</h2>
main 公開するものを置くブランチ
develop 開発中のものを置くブランチ
release 次にリリースするものを置くブランチ
feature-\* 新機能開発中に使うブランチ
hotfix-\* 公開中のもののバグ修正用ブランチ

<h2 id="commit-message">コミットメッセージの記法</h2>
init (first commit)
setup (プロジェクトのセットアップ)
add: 新規(ファイル、機能)
update: 機能修正(バグではない)
perf: パフォーマンスを向上させるためのコード変更
clean: 整理(リファクタリング等)
change: 仕様変更
fix: バグ修正
remove: 削除(ファイル、機能)
revert: 変更取り消し
test: 不足しているテストの追加や既存のテストの修正
sleep: i'm so sleepy
