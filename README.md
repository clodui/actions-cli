# GitHub Action for Clodui

This GitHub action helps to run Clodui CLI commands from your workflow. Learn more about Clodui CLI from the docs https://www.clodui.com/docs/clodui-cli/

### Usage

Example GitHub workflow file which shows deploying changes to a website.

```yaml
name: "Deploy Website"

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Deploy to Clodui
        uses: clodui/actions-cli@v2.0
        with:
          username: ${{ secrets.CLODUI_USERNAME }}
          password: ${{ secrets.CLODUI_PASSWORD }}
          website-id: ${{ secrets.WEBSITE_ID }}
          source-dir: ./sample/test-website/
          publish: publish
```

### Options

- `username` : Clodui username; best practice is to read it from [secrets]
- `password` : Clodui password; best practice is to read it from [secrets]
- `website-id` : Id of your Clodui website
- `source-dir` : Path to the directory from files to be uploaded. Please make sure it is set as a relative path to your workspace (`GITHUB_WORKSPACE`)
- `publish` : Option for controlling automatic publishing. Valid values are `publish` or `no-publish`

[secrets]: https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets
