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
        uses: clodui/actions-cli@v1
        with:
          args: >
            --username ${{ secrets.CLODUI_USERNAME }}
            --password ${{ secrets.CLODUI_PASSWORD }}
            deploy
            create
            --website-id ${{ secrets.WEBSITE_ID }}
            --source-dir ./sample/test-website/
```

**Note :** Clodui CLI argument `source-dir` is set as a relative path to the environment `GITHUB_WORKSPACE`
