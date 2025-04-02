## MkDocs

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
- テンプレートの上書き https://www.mkdocs.org/user-guide/customizing-your-theme/
- 拡張機能の有効 https://dev.classmethod.jp/articles/mkdocs-plugins-1/
- デプロイにカスタムドメインの設定 https://www.mkdocs.org/user-guide/deploying-your-docs/
    - mkdocsのCNAME https://github.com/mkdocs/mkdocs/blob/master/docs/CNAME

## GitHub Pages

- MkDocsのでデプロイ https://www.mkdocs.org/user-guide/deploying-your-docs/
- `mkdocs gh-deploy` で認証を求められ、パスワード入力で失敗する
    - GitHubアカウントのClassic tokenを使って認証を通過する https://qiita.com/NumLock7019/items/c867e01c5451dc7d06e3
- 取得したドメインにDNSを設定して、GitHub Pagesにカスタムドメインとして設定する https://qiita.com/eshun-mikuro-tama/items/8fc3cfceab3281a8c24f