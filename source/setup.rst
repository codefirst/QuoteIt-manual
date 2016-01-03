セットアップ
==================================================

ここでは、インハウスに QuoteIt をデプロイする方法を説明します。
QuoteIt で、インハウスのリソースを引用したい場合に参照してください。
そうでない場合には、Heroku 版の QuoteIt_ を利用してください。

動作環境
--------------------------------------------------
QuoteIt を利用するためには、以下のソフトウェアが必要です。

* Ruby 2.0.0 or later
* Bundler 1.3.5 or later
* PostgreSQL 9.3 or later

デプロイ方法
--------------------------------------------------
1. QuoteIt をダウンロードします。
::

    $ git clone git://github.com/codefirst/QuoteIt.git

2. 必要な gem をインストールします。
::

    $ bundle install --path .bundle --without development test

3. アセットをコンパイルします。
::

    $ bundle exec rake assets:precompile RAILS_ENV=production

4. DB をセットアップします。
::

    $ bundle exec rake db:migrate RAILS_ENV=production
    $ bundle exec rake db:seed

5. QuoteIt を立ち上げます。
::

    $ bundle exec rails s -e production

6. QuoteIt にアクセスします。
::

    http://localhost:3000

プラグインの追加
--------------------------------------------------
インハウスにデプロイした QuoteIt へのプラグインの追加は config/quote_it.json に追記をしたのち、
以下の rake タスクを実行します。

::

    $ bundle exec rake db:seed

Heroku QuoteIt へのリレー
--------------------------------------------------
インハウス QuoteIt で処理されなかった URL を Heroku QuoteIt_ へ
移譲することもできます。

以下の設定を config/quote_it.json に追記します。

::

    {
      "regexp": "(.+)",
      "clip": "https://quoteit.herokuapp.com/clip.html?u=$$1",
      "transform": "content",
      "service": {
        "name": "QuoteIt",
        "url": "https://quoteit.herokuapp.com/"
      }
    }

DB に登録します。

::

    $ bundle exec rake db:seed

.. note::

   QuoteIt は、プラグインが登録された順に処理をしていくため、
   QuoteIt プラグインは必ず最後に登録して下さい。

.. _QuoteIt: https://quoteit.herokuapp.com/
.. _debeso: https://www.codefirst.org/debeso/
