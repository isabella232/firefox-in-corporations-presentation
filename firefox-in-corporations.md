# 法人利用におけるFirefox

subtitle
:   　　
    ～ カスタマイズから集中管理まで ～

author
:   株式会社クリアコード

allotted_time
:   50m

theme
:   clear-code


# 株式会社クリアコード

![](images/ClearCodeCI-with-letter.png){:relative_height="100"}

{::comment}

# 株式会社クリアコード

概要

![](images/company-history.png){:relative_height="100"}

# 株式会社クリアコード

主な事業内容

![](images/company-categories.png){:relative_height="100"}

# 株式会社クリアコード

主な事業内容

![](images/company-categories2.png){:relative_height="100"}


{:/comment}

# 株式会社クリアコード

Mozillaサポート

![](images/company-mozilla-support.png){:relative_height="100"}



# 基礎知識

 * Firefoxのリリースサイクル
 * 法人利用における
   Firefox採用の利点

# リリースサイクル

通常版と長期サポート版の2ライン

![](images/mozilla-release-lines.png){:relative_height="100"}

{::comment}
画像は
http://www.mozilla.jp/business/downloads/
より引用
{:/comment}

# リリースサイクル

通常版
:   * サポート期間は6〜8週間

長期サポート版（*ESR版*）
:   * 主に企業利用を想定
    * サポート期間は約1年、
      通常リリースと同期して
      セキュリティアップデート

# どこで使われている？

 * 生命保険・損害保険
 * 電力会社
 * 中央官庁

その他、様々な企業で利用実績あり

# なぜ使われる？

 * 現在利用中のシステムを
   維持したままで
 * 自由に導入・削除ができて
 * 最新のWeb技術に対応している

**「ちょうどいい」選択肢**
として重宝されている

# 代表的な導入の動機

事例1
:   SaaSを利用したい
    （サービスがモダンなWebブラウザを要求）

     * Office 365
     * Google Apps
     * Salesforce

# 代表的な導入の動機

事例2
:   古いInternet Explorerに依存した
    社内システムの更新が間に合わない
    
     * IEは社内ネットワーク用に限定
     * インターネットはFirefoxで利用

# 導入までの流れ（例）

 * 仕様検討
   * 運用中のIEと同様の管理について相談
   * IEとFirefoxの使い分けなど、
     要件を満たすカスタマイズの提案
   * おすすめ設定の提示
 * α版、β版提供
 * 正式版提供、全社展開


# カスタマイズの実例

デモ


# 保守・メンテナンス

導入後に実際に必要になる事

 * バージョンアップへの対応
 * トラブル発生時の対応

# バージョンアップへの対応

 * 旧バージョンで使用していた
   設定の新バージョンでの検証
 * 新バージョンで使えなくなった
   機能・設定の代替方法の調査
 * 更新が停止した既存アドオンの
   取り扱いの判断

# 参考となる公開情報

 * [リリースノート](https://www.mozilla.jp/firefox/releases/)
 * [Firefox サイト互換性情報](https://www.fxsitecompat.com/ja/)
 * [開発者向けリリースノート](https://developer.mozilla.org/ja/Firefox/Releases)
 * [Mozilla Japanブログ](https://www.mozilla.jp/blog/)
 * [Firefox自体のソースコード](http://mxr.mozilla.org/)

# インシデントサポート事例

 * ソースコードの調査まで含めた
   原因究明と回避策の提案
   * 問題を暫定的に回避する
     アドオンの提供
   * 場合によってはMozilla Japanに
     エスカレーション
 * 更新が停止した既存アドオンを
   新バージョン向けに改修



# 法人利用で便利な特性

![](images/screenshot-menu-blur.png){:relative_height="100"}

# Firefoxの特徴

カスタマイズ性が*非常に高い*
:   * できる事の幅が広い
    * ともすれば途方に暮れがち
    * *指針*を元に考えよう

# IEの運用の延長線上で

 * IEでは○○していた
 * IEでは○○できた

→これを手がかりに考える
:   * 実際にやっている・やっていた事は
      イメージしやすい

# 頻出カスタマイズ例

![](images/screenshot-menu-blur.png){:relative_height="100"}


# 例：使わない機能の無効化

 * 自動アップデートを禁止したい
 * アドオンを利用させたくない

→*アドオン*を使用
:   * Disable Auto-update
    * Disable Addons

# 例：アドオンの強制使用

 * 自社開発のアドオンを使いたい
 * 古いアドオンを使いたい

→*MCD*を使用

~~~
lockPref("xpinstall.signatures.required", false);
lockPref("extensions.checkCompatibility.45.0", false);
~~~
{: lang="javascript"}

# 例：プライバシー情報の制御

 * パスワードを保存させたくない
 * 位置情報を提供させたくない

→*MCD*を使用

~~~
lockPref("signon.rememberSignons", false);
lockPref("geo.enabled", false);
~~~
{: lang="javascript"}

# 例：通信量の削減

 * バックグラウンドで行われる
   不要な通信をすべて禁止したい

→*MCD*を使用

~~~
lockPref("geo.wifi.uri", "");
lockPref("loop.enabled", false);
~~~
{: lang="javascript"}

# 例：プラグインの制御

 * プラグインを強制的に有効化/無効化したい

→*アドオン*を使用
:   * Force Addon Status

# 例：UIの制御

 * 特定のメニュー項目を隠したい
 * 特定のキーボードショートカットを
   無効化したい

→*アドオン*を使用
:   * globalChrome.css
    * UI Text Overrider

# 例：設定の集中管理

 * 設定を変更させたくない
 * グループポリシーのように
   組織全体で設定を一括管理したい

→*MCD*を使用

~~~
lockPref("設定キー", "値");
~~~
{: lang="javascript"}

# 管理者による設定の強制

![](images/figure-local-mcd.png){:relative_height="60"}

Firefoxの実行ファイルと同じ
フォルダにある設定ファイルを参照

# グループポリシーのような運用

![](images/figure-remote-mcd.png){:relative_height="75"}

サーバー上にある設定ファイルを参照



# 例：インスタンスの使い分け

 * 「組織内システム用」と
   「通常用」を使い分けたい
 * サポートセンターで
   「業務システムの閲覧用」と
   「お客様の環境の再現用」を
   使い分けたい
 * 特定Webサイト用ビューワーとして使いたい


# 例：インスタンスの使い分け

![](images/screenshot-multiple-versions.png){:relative_width="40" align="right" relative_margin_right="-10"}

→*専用プロファイル*の使用
:   * 複数バージョン共存
    * 複数プロセスを
      並行起動
    
    ```
    > "C:\Program Files (x86)\Mozilla Firefox\firefox.exe"
        -no-remote -profile "C:\Path\To\Profile"
    ```

# その他様々なカスタマイズ

 * SQLite DBを自動的にVACUUMさせたい
 * 特定のタブだけをアイドル時に
   再読み込みさせたい

→*アドオン*を開発
:   * Places Auto Vacuum On Idle
    * Reload on Idle


# 自社開発アドオンの導入時

 * 非公開のアドオンとして
   Mozilla Add-onsに登録
 * 設定で署名の検証を無効化
   
   ~~~
   lockPref("xpinstall.signatures.required", false);
   ~~~

# 例：一斉展開

 * カスタマイズ済みのFirefoxを
   一斉展開したい

→*メタインストーラ*を使用
:   * Firefox本体をサイレントインストール
    * カスタマイズを反映
    * 詳細は[www.clear-code.com/blog/2012/11/7](http://www.clear-code.com/blog/2012/11/7.html)を参照


# メタインストーラの動作

![](images/figure-meta-installer.png){:relative_height="75"}

カスタマイズを自動的に反映


# まずはここから

![](images/screenshot-tech-faq-blur.png){:relative_width="100"}

# カスタマイズメニュー

![](images/screenshot-menu.png){:relative_width="45" align="right" relative_margin_right="-10"}

各種カスタマイズ項目の*メニュー*

 * 何ができる？
 * どんな選択肢
   がある？

実際の導入事例の
頻出設定パターン集

→*[github.com/clear-code/firefox-support-common](https://https://github.com/clear-code/firefox-support-common/)*


# メタインストーラ例

冒頭のデモに使用した
Firefox 45のカスタマイズ例

→*[github.com/clear-code/firefox-support-common](https://https://github.com/clear-code/firefox-support-common/)*

ビルド済みファイルは
[Releasesからダウンロード可能](https://github.com/clear-code/firefox-support-common/releases/tag/v45.0)



# 法人向けFAQ

![](images/screenshot-tech-faq.png){:relative_width="35" align="right" relative_margin_right="-10"}

[mozilla.jp/business/faq/tech/](http://mozilla.jp/business/faq/tech/)
([github.com/mozilla-japan/enterprise](https://github.com/mozilla-japan/enterprise/))

 * ○○を無効化したい
 * ○○を使いたい

*公開中*

# サポートサービス

株式会社クリアコード
:   * [www.clear-code.com](http://www.clear-code.com)
    * Mozilla Japanサポートパートナー
    * Firefox/Thunderbird
      インシデントサポート

{::comment}
このスライドは外す？
{:/comment}
