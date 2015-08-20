CS部 勉強会 ![CS](https://github.com/dit00091/cs_study/blob/master/cs_image.png)
===

# 2015/08/21 Git編第2回
## はじめに

* 今回の勉強会もGitについてやります！
    * 伊藤さんによるGit編第1回のかっけースライド資料は[こちら](https://docs.google.com/presentation/d/1UwohUro-f0SAuYdq5C9y7Rx1Lc2jAfOUmp8ilMolYNA/edit?pli=1#slide=id.p)。

## 内容

* 第1回でユースケース毎の使用コマンド例を上げてくれていたので、私が客先のプロジェクトでどんな感じでやってますよーって言うのを紹介します。
    * Gitって何だろう？（さわりだけね）
    * 開発プロジェクトでの導入
    * よく使うコマンド
    * ブランチ運用
    * 時間が余ったらMarkdownでも

## Gitって何だろう？

* バージョン管理システムです。
    * 読んで字のごとくファイルのバージョンを管理してくれます。
        * 履歴が残るし古いファイルとのdiffが見れたり便利ですってことらしい。
        * どんなタイプのファイルでも管理してくれる素敵なファイルシステムです。
    * 複数人での開発するのに便利です。
        * 修正対象のファイルが被っても強制上書きせずに警告が出て教えてくれたりします。

* ついでにgithubってなんだろう？
    * git開発プロジェクト用のウェブサービスです。
        * 視覚的にソースコードや履歴等が見れて便利。
        * コマンドラインからコマンドを打たなくてもある程度の操作が可能。（かわりにそのコマンドを忘れます！）
        * レビューに便利なプルリクエスト。
        * 課題管理はイシューを使う。
        * 後はグラフのネットワークも便利。

* さらについでにSourceTreeってなんだろう？
    * Gitの無料クライアントです。ちょこちょこ使ってます。
    * GUIでコマンドまったく打つ必要がない。
        * ゆえにコマンド覚えない弊害が。コマンド打てないと小馬鹿にされるので注意。
    * 他にも色んなのがある。
        * Git Gui（Windows / Mac）：Git公式クライアント
        * Github for Windows、Github for mac：Github公式クライアント
            * 8/13にGitHub Desktopってのが公開されたらしい。既存の「GitHub for Windows」および「GitHub for Mac」を統合した後継ツール。WindowsおよびMacに対応するフリーソフトで、公式サイトからダウンロードできる。
            * まあ、まだ試してません。
        * などなど

## 開発プロジェクトでの導入

* Pro Git
    * 無料電子書籍
    * まず読め！って言われる。話はそれからなんですって。
        * https://progit-ja.github.io/
    * でも量が多すぎる。こまめにね。

## よく使うコマンド紹介

* 伊藤さんとあまり変わりません。
    * init
    * clone
    * checkout
    * fetch
    * branch
    * status
    * diff
    * log
    * commit
    * push
    * merge
    * stash
    * reset
* まったく使ってなかったけど目からウロコ
    * grep
        * 伊藤さんスライド見て、こんなんあったんだなーと。ちょー便利。常識だったのかな？

## ブランチ運用

* の前に環境の整理から
    * PRD環境：商用環境
    * STG環境：商用リリース前の検証用環境
    * DEV環境：開発用環境
    * local環境：自分のPC内の環境

* ブランチ運用
    * masterブランチ
        * 現在の商用環境のソース群を管理
        * PRD環境に対応
    * stagingブランチ
        * 商用リリース前のソース群を管理し、最終的な検証に利用
        * STG環境に対応／PRD環境と同構成のサーバー
    * developブランチ
        * 開発用のソース群を管理し、loaclで開発したfeature、hotfix用ブランチをマージして検証に利用
        * DEV環境に対応／サーバーの台数やインスタンスタイプ等、最小構成のサーバー
    * featureブランチ
        * 仕様追加や仕様変更、積み残し対応等、定期開発用のブランチ
        * feature/xxxxxといった名前で作成
    * hotfix(bugfix)ブランチ
        * バグ対応等緊急性の高い開発用のブランチ
        * hotfix/xxxxxといった名前で作成

### 基本的な作業の流れ

1. local環境でmasterブランチ（他のブランチの場合もあり）からfeatureまたはhotfixブランチを作成
2. local環境で開発作業、単体試験を実施
3. featureまたはhotfixブランチをdevelopブランチにpush＆merge
4. DEV環境で結合試験を実施
5. developブランチをstagingブランチにmerge
6. STG環境で結合試験、総合試験を実施
7. stagingブランチをmasterブランチにmerge
8. masterブランチにtag付けしてPRD環境にリリース

![al2](https://github.com/dit00091/cs_study/blob/master/al2.png)

## Markdownって何？

* 文書を記述するための軽量マークアップ言語のひとつ。 もとはプレーンテキスト形式で手軽に書いた文書からHTMLを生成するために開発された。(by Wikipedia)
    * textで簡単にHTMLをwikiっぽく作れますよって話です。
    * gitのREADMEがこのMarkdownって形式です。つまりこの資料。（README.md）


* 使ってるエディタをMarkdownに対応させたり、新しいエディタをインストールするのって面倒じゃない？
    * 今回の資料を作るのに家パソに[Haroopad](http://pad.haroopress.com/user.html)ってのを入れてみた。
    * 公式サイトでダウンロード＆インストールするだけ。
    * リアルタイムで変換後のHTML見れるし、記法ヘルプも見れる。
    * アプリ起動後、数秒で感覚的に使えるから、なかなか良いっぽいよ。