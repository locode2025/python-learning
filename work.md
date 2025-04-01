## MkDocsのインストール

- チュートリアル https://www.mkdocs.org/getting-started/
    - `pip3 install mkdocs`
    - `%mkdocs` -> `zsh: command not found: mkdocs` ... pythonのパスが通っていない
    - `% echo $path ` ... Pythonのパスがないことを確認
    - ユーザディレクトリ直下に `.zshrc` を作成
    - パスを追記
        - `vi ~/.zshrc`
        - `export PATH="$HOME/Library/Python/3.9/bin:$PATH"`
    - 設定の反映 `source ~/.zshrc`
    - パスが通っていることを確認 `mkdocs --version`
- テーマ https://github.com/mkdocs/mkdocs/wiki/MkDocs-Themes
    - 複数のテーマを選択できる https://mkdocs.github.io/mkdocs-bootswatch