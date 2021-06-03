# code-review-test

## 1) 코드리뷰 브랜치 아키텍쳐 자동화
https://blog.kshgroup.kr/code-reviews-for-existing-code-with-github/

## 2) 커밋 시, 리뷰 브랜치를 자동으로 생성 후 lint 적용 점수 도출

```yml
  
# This is a basic workflow to help you get started with Actions

name: CI

# Controls when the action will run. 
on: push

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2

      # Runs a single command using the runners shell
      - name: Run a one-line script
        run: echo Hello, world!

      # Runs a set of commands using the runners shell
      - name: Create Branch GitHub Action
        uses: peterjgrainger/action-create-branch@v2.0.1
        env:
          GITHUB_TOKEN: ${{ secrets.REVIEW }}
        with:
          branch: 'code-review-branch'
          
      # git checkout branch 
      - uses: actions/checkout@v2
        with:
          ref: code-review-branch
          
      - name: Install Requirements
        run: |
          python -m pip install --upgrade pip
          pip install pylint
          
      #The final step runs pylint on all of the python files in the repository.
      - name: Analysing the code with pylint
        run: |
          pylint src/
```
