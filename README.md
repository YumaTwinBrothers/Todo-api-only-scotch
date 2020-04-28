# README

* APIモードで新規プロジェクト作成（デフォルトのテストフォルダは作成しない..-T付与）
    $ rails _5.2.4.1_ new todos-api --api -T

* RSpec関連のgemをインストール
    group :development, :test do
      gem 'rspec-rails', '~> 3.5'
    end
    group :test do
      gem 'factory_bot_rails', '~> 4.0'
      ←factory_girl_railsではなくfactory_bot_railsをインストール
      gem 'shoulda-matchers', '~> 3.1'
      gem 'faker'
      gem 'database_cleaner'
    end  

* RSpecインストール後、factories(テストデータ格納)ディレクトリ作成

* spec/rails_helper.rbを編集（追加するコードの場所に注意）

* モデルを作成し、spec内のmodelテストを書いてその通りにmodelを実装

* コントロールを作成し、spec/requestsディレクトリ作成後にテストファイル作成し、factoriesのテストデータ定義後にリクエストのテストを書いていく
その通りにコントロールを実装
←Request specs

* コントローラーの実装は少し特殊で、
コントローラーで使用するjson_responseメソッドをconcerns/response.rbのmodule Responseに定義しレスポンス内容を指定
concerns/exception_handler.rbのmodule ExceptionHandlerに例外処理を記載
application_controller.rbにResponseとExceptionHandlerをincludeする

* クライアントツールのhttpieでデータ処理の確認
