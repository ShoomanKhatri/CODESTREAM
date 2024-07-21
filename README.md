## ##Learning use of  Github Actions##

Note:  Use 3 backticks to write code which can be copied.
This code directly append without waiting.


```
name: Update Text File

on:
  push:
    branches:
      - main  # Adjust the branch name as needed

jobs:
  commit:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Add or Delete Text File
        run: |
          echo "This is a simple text file." >> example.txt  # Append instead of overwrite
          # echo "" > example.txt  # Use this line to delete the contents of the text file

      - name: Set Git Config (Optional).
        run: |
          git config --global user.email "shoomankhatri@gmail.com"
          git config --global user.name "shoomankhatri" || true  # Handle potential errors (optional)

      - name: Commit and Push
        run: |
          git add example.txt
          git commit -m "Update example.txt"  # Consider more descriptive commit messages
          git push https://github.com/${{ github.repository }} HEAD:${{ github.ref }} || true  # Handle potential errors (optional)
        env:
          GH_TOKEN: ${{ secrets.MY_ACCESS_TOKEN }}  # Use your secret name here.

```




