- インストール済みのRailsのバージョン確認
```
gem list rails
```

- 指定のバージョンでRailsコマンドを実行
```
rails _6.0.3_ -v
```
アンダースコアでバージョンを囲むことで、指定したバージョンのRailsコマンドを実行できる。
```
rails _6.0.3_ new hello_rails
```

- binディレクトリ
Railsアプリケーションを開発するために利用する実行コマンドを格納しているディレクトリになる。
通常Bundlerを使用して依存関係を解決している場合には、その依存関係を解決した上で実行するために以下をつける。
```
bundle exec rails
```
しかし、railsでは利便性や一貫性のためこれをつけなくても実行できるコマンドをbinディレクトリに用意している。
このようなファイルをbinstubと呼ぶ。
コマンド実行の一貫性を持たせるためにRailsプロジェクト内で扱う実行コマンドはbinディレクトリに集約している。

旧来はrailsコマンドに続いてrakeコマンドもよく利用していましたが、現在はrakeコマンドで実行できるRakeタスクは
railsコマンドから実行できるように統合が進められているため、rakeコマンドを直接利用する頻度は少なくなっている。

- configディレクトリ
database.yml: DBへの接続情報を定義する。

- 利用可能なrailsコマンドの一覧を表示する。
```
bin/rails -h
```

- 具体的なコマンドについてさらに詳しいヘルプを見る。
```
bin/rails s -h
```

```
ls -la 1_3/hello_rails/
```
ls: これは "list" の略で、ディレクトリの内容を表示する基本的なコマンドです。

-l: このオプションは "long format" を意味します。つまり、ファイルやディレクトリの詳細な情報（パーミッション、所有者、グループ、サイズ、最後の変更日時など）を表示します。

-a: このオプションは "all" の略で、すべてのファイルやディレクトリを表示します。デフォルトでは、. で始まる隠しファイルやディレクトリは表示されませんが、このオプションを使用することで表示されるようになります。

1_3/hello_rails/: この部分はコマンドの対象となるディレクトリを指定しています。この場合、現在のディレクトリからの相対パスで 1_3/hello_rails/ ディレクトリを指しています。



サブディレクトリの.gitを一時的に移動:

この方法は、一時的に問題を回避するためのものです。もし1_3/hello_rails/が別のGitリポジトリとしての意味を持っている場合は、後で元に戻す必要があります。
```
mv 1_3/hello_rails/.git 1_3/hello_rails/.git_backup
```
再度git addを試す:

```
git add 1_3/
```
もし2の手順でサブディレクトリの.gitを移動した場合、後で元の位置に戻してください。

```
mv 1_3/hello_rails/.git_backup 1_3/hello_rails/.git
```
この方法で問題を一時的に解決できるかもしれません。ただし、1_3/hello_rails/が別のGitリポジトリとしての意味を持っている場合、サブモジュールとして正しく追加する方が良いでしょう。サブモジュールについては、Gitの公式ドキュメントなどで詳しく学ぶことができます。


