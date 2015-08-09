CS部 勉強会 ![CS](https://github.com/dit00091/cs_study/blob/master/cs_image.png)
===

# 2015/08/21 git編第2回

## 内容

* 第1回でユースケース毎の使用コマンド例を上げていたので、私が客先のプロジェクトでどんな感じでやってますよーって言うのを紹介します。
    * gitって何だろう？（さわりだけね）
    * よく使うコマンド
    * ブランチ運用
    * 時間が余ったらMarkdownでも

## gitって何だろう？

* バージョン管理システムです。
    * 読んで字のごとくバージョン管理してくれます。
        * 履歴が残るし古いファイルとのdiffが見れたり便利ですよと。
    * 複数人での開発するのに便利です。
        * 修正対象のファイルが被っても強制上書きせずに警告がでて教えてくれます。

* ついでにgithubってなんだろう？
    * git開発プロジェクト用のウェブサービスです。
        * 視覚的にソースコードや履歴等が見れて便利。
        * どんなタイプのファイルでも管理してくれる素敵なファイルシステムです。
        * コマンドラインからコマンドを打たなくてもある程度の操作が可能。（かわりにそのコマンドを忘れます！）

## よく使うコマンド紹介

* 基本編
    * git clone
    * git checkout
    * git 

## ブランチ運用

* master
    * 現在の商用環境のソース群を管理
    * PRD環境に対応
* staging
    * 商用リリース前のソース群を管理し、最終的な検証に利用
    * STG環境に対応／PRD環境と同構成のサーバー
* develop
    * 開発用のソース群を管理し、loaclで開発したfeature、hotfix用ブランチをマージして検証に利用
    * DEV環境に対応／サーバーの台数やインスタンスタイプ等、最小構成のサーバー
* feature
    * 仕様追加や仕様変更、積み残し対応等、定期開発用のブランチ
    * feature/xxxxxといった名前で作成
* hotfix
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

## Markdownって何？

* 文書を記述するための軽量マークアップ言語のひとつ。 もとはプレーンテキスト形式で手軽に書いた文書からHTMLを生成するために開発された。(by Wikipedia)
    * textで簡単にHTMLをwikiっぽく作れますよって話です。
    * gitのREADMEがこのMarkdownって形式です。つまりこの資料。（README.md）

---

* 使ってるエディタをMarkdownに対応させたり、新しいエディタをインストールするのって面倒じゃない？
    * 今回の資料を作るのに家パソに[Haroopad](http://pad.haroopress.com/user.html)ってのを入れてみた。
    * 公式サイトでダウンロード＆インストールするだけ。
    * リアルタイムで変換後のHTML見れるし、記法ヘルプも見れる。
    * アプリ起動後、数秒で感覚的に使えるから、なかなか良いっぽいよ。