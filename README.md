# 맥에서 nvm, npm, node 설치 #
[버젼별 설치 사이트 : https://nodejs.org/en/download](https://nodejs.org/en/download) \
npm 설치 후 express, yarn 설치
```bash
% npm install express   => 설치
% npm install yarn      => 설치
```
<br>

# github test #
## vscode에서 github로 올리기 ##

```bash
% git init
    //참고
    % git config --global user.name "idevkim"
    % git config --global user.email "idevkim@naver.com"
    % git config --global http.postBuffer 524288000
% git add .
% git commit -m "first commit"
% git branch -M main
% git remote add origin https://github.com/idevkim/vscode_to_github.git
% git push -u origin main
```

## git branch 기록 ##
기본은 도움말은 <code> % git branch -h </code>
```bash
% git branch -r => 사용중인 목록
% git branch -M 브랜치명 => 브랜치 설정
```

## bash :: 코드형태로 ##
예시
```bash
# Clone this project
git clone https://github.com/devenes/node-js-dummy-test
```

## git pages ##
`gh-pages`를 사용하여 깔끔하게 branch/forlder 변경하기. (기본: main/root) 또는 master \
`gh-pages`가 없으면 아래와 같이 추가하자.
```bash
git branch gh-pages
```
`gh-pages`를 초기화.
``` bash
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "Init gh-pages branch"
git checkout main(master)
```
`git worktree`을 사용하여 브랜치를 하위 디렉토리로 마운트합니다.
``` bash
git worktree add dist gh-pages
```
`dist`폴더를 무시하지 않은 경우 생성된 파일을 실수로 `main(master)`브랜치 커밋에 추가하지 않도록 폴더를 무시하세요.
``` bash
echo "dist/" >> .gitignore
```

### 배포(Deploy) ###
매번 `bundle`를 빌드 후 생성된 파일은 `dist`폴더에 있다. \
`dist`폴더가 이제 `gh-pages`브랜치이므로 커밋을 만들고 푸시하기만 하면 바로 배포할 수 있습니다.
``` bash
cd dist
git add --all
git commit -m "Deploy on gh-pages updated"
git push origin gh-pages
```

이렇게 하면 `main(master)`지점 기록에 아무것도 추가되지 않아 깔끔하게 유지됩니다.

## pull ##
```bash
% git pull origin main --rebase  
```
