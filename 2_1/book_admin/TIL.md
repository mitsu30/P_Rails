##  2章

```
class AddPublisherIdToBooks < ActiveRecord::Migration[6.0]
  def change
    add_reference :books, :publisher, foreign_key: true
    change_column :books, :publisher_id, :integer, null: false
  end
end
```

`:integer`の部分はpublisher_id カラムのデータ型を整数型 (integer) として指定していることを示しています。


## `rails db:migrate:reset`

以下の二つのコマンドを合わせたもの
- `rails db:drop`
- `rails db:migrate`


## `rails db:reset`

以下の二つのコマンドを合わせたもの
- `rails db:drop`
- `rails db:setup`
db:reset はマイグレーションファイルを編集しても、その内容は反映されない。

## `rails db:drop`
Railsアプリケーションで使用しているデータベースを削除するタスクです。

データベースの削除: rails db:drop を実行すると、現在の環境（デフォルトでは開発環境）のデータベースが完全に削除されます。これにより、そのデータベースに保存されている全てのデータも失われます。

環境の指定: 特定の環境のデータベースを削除する場合、RAILS_ENV 環境変数を使って環境を指定できます。例えば、テスト環境のデータベースを削除する場合は、RAILS_ENV=test rails db:drop のようにコマンドを実行します。

複数のデータベース: Rails 6からは、複数のデータベースの使用がサポートされています。この場合、rails db:drop は全てのデータベースを削除する可能性があります。

注意: rails db:drop はデータベースを削除する危険な操作です。実行前にデータベースのバックアップを取ることや、何をしているのかを確認することが非常に重要です。特に、本番環境でこのコマンドを誤って実行すると大きな問題を引き起こす可能性があります。

総じて、rails db:drop はデータベースを削除するタスクであり、注意深く使用する必要があります。


## `rails db:setup`
Rails アプリケーションのデータベースをセットアップするためのタスクです。

rails db:create - データベースを新しく作成します。
rails db:schema:load または rails db:structure:load - db/schema.rb もしくは db/structure.sql の内容に基づいてデータベースのスキーマをロードします。これにより、マイグレーションファイルを実行することなくデータベースの構造を早く構築することができます。
rails db:seed - db/seeds.rb ファイル内のコードを実行し、データベースに初期データを投入します。
このコマンドの使用ケースとしては、新しい環境や新しいマシンでRailsプロジェクトをセットアップするときや、データベースを一から再構築する際に利用されます。

注意点として：

rails db:setup は既存のデータベースを削除するわけではないので、既存のデータベースがある場合はそれを上書きするわけではありません。しかし、スキーマや初期データをロードすることで、データベースの状態が変更される可能性があります。
このコマンドを本番環境で使用する際には注意が必要です。特に、初期データの投入やスキーマの変更が本番環境に影響を与える可能性があるためです。


## `rails db`

データベースのCLI（Command-Line Interface）ツールを起動します。具体的には、使用しているデータベースの対話的なコンソールを開始するのに使用されます。

例えば：
SQLite3: コマンドはSQLiteのコンソールを起動します。
PostgreSQL: psql というPostgreSQLのコンソールクライアントを起動します。
MySQL: mysql コマンドラインクライアントを起動します。
このコマンドは、データベースの設定やデータを直接調べたり、手動でSQLクエリを実行する際に非常に便利です。Railsが使用するデータベースに応じて適切なCLIツールを起動します


## `matz.reload.books.count`

reloadはActiveRecordのインスタンスメソッドで、データベースから最新のデータを再取得して、そのオブジェクトの属性を更新します。これは、オブジェクトがメモリ内で古い状態のままで、データベースの現在の状態と同期させるために使われることが多いです。


## `book.reload.authors.pluck(:name)`
pluck(:name): pluck は ActiveRecord のメソッドで、指定したカラムの値を配列として取得します。この場合、authors に関連付けられたすべての著者の name カラムの値を配列として取得します。
