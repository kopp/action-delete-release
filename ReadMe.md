# Delete an existing release before re-creating it


```yml
name: Main

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Delete
        uses: kopp/action-delete-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITHUB_REPOSITORY: ${{ github.repository }}
        with:
          tag_name: tag-here

      - name: Release
        uses: softprops/action-gh-release@v1
        with:
          name: type-your-release-name
          tag_name: tag-here
```
