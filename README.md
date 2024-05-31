# Auto Update D-Day Label GitHub Action

This GitHub Action updates D-Day labels in your repository according to the specified rules.

## Usage

To use this action, add the following step to your workflow YAML file.

## Example Workflow

Create a file named `update_labels.yml` in the `.github/workflows` directory of your repository with the following content:

```yaml
name: auto-update D-Day labels

on:
  schedule:
    - cron: '1 15 * * *'  # 매일 한국 시간 00:01에 실행

jobs:
  call-workflow:
    runs-on: ubuntu-latest
    steps:
      - name: use update_d_label
        uses: torder-lkj/update_d_label@v1.0.3 # Please make sure to use the latest version.
        with:
          github_token: ${{ secrets.TOKEN }}
```
Please make sure to replace secrets.TOKEN with your actual GitHub token.

## Note
- This action will only run if there are labels starting with "D-".
- If there are no labels starting with "D-", the action will not execute.
- Labels with "D-0" will not be updated.
- The action will update the D-Day labels by decrementing them by 1 every time it runs.
