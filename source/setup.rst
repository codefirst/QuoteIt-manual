セットアップ
==================================================

ここでは、インハウスに QuoteIt をデプロイする方法を説明します。
QuoteIt で、インハウスのリソースを引用したい場合に参照してください。
そうでない場合には、Heroku 版の QuoteIt_ を利用してください。

動作環境
--------------------------------------------------
QuoteIt を利用するためには、以下のソフトウェアが必要です。

* Ruby 1.9.2
* Bundler 1.0.7 or later
* MongoDB 1.8.1 or later
* memcached 1.4.9 or later

デプロイ方法
--------------------------------------------------
1. QuoteIt をダウンロードします。
::

    $ git clone git://github.com/codefirst/QuoteIt.git

2. MongoDB を立ち上げます。
::

    $ mongod --dbpath <dir_name>

3. memcached を立ち上げます。
::

    $ memcached -vv

4. 必要な gem をインストールします。
::

    $ bundle install --path vendor/bundle

5. QuoteIt を立ち上げます。
::

    $ bundle exec padrino start

6. QuoteIt にアクセスします。
::

    http://localhost:3000

プラグインの追加
--------------------------------------------------
インハウスにデプロイした QuoteIt へのプラグインの追加は CUI から行います。
ここでは例として debeso_ を引用するプラグインを作成します。

**T.B.D**

.. _QuoteIt: http://quoteit.heroku.com/
.. _debeso: http://www.codefirst.org/debeso/
