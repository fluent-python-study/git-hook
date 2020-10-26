# Project Meat 
## Workflow
### 초기 설정
1. `git-hook` 레포지토리를 `clone`합니다.
2. 해당 파트의 레포지토리를 `clone`합니다. 파트별 레포지토리는 분석과 개발 각각  `project-meat-chatbot-ml`과 `project-meat-chatbot-be`입니다. 이때 유의사항은, `git-hook` 디렉토리 안에 해당 파트의 레포지토리를 `clone` 받거나, 해당 파트 레포지토리 안에 `git-hook` 레포지토리를 `clone` 받지 않아야 한다는 점입니다.
3. `clone` 받은 파트별 레포지토리의 `master` 브랜치에 `README.md`와 `.gitignore` 파일을 생성한 후 원격에 `push`합니다. 3을 완료할 경우 base branch가 `master`로 설정됩니다.
4. 파트별 레포지토리의 root (e.g. `~/project-meat-chatbot-be`)에서 `cp ~/githook/utils .` 명령어를 실행해 `utils` 파일을 파트별 레포지토리로 복사합니다. 이때 `.gitignore` 파일에 `utils` 파일을 추가해줍니다.
5. utils 파일의 `PROJECT_NAME` 값을 프로젝트에 맞게 수정해줍니다. e.g. 분석: `ML`, 개발 `BE`
6. `source utils` 명령어를 실행해 필요한 변수와 함수를 선언해줍니다. `~/.bashr` 또는 `~/.zshrc` 파일에 해당 명령어를 저장해둘 경우 매번 5를 실행하지 않아도 됩니다.
7. 프로젝트 최상위 폴더에서 `cp prepare-commit-msg .git/hooks/.` 명령어를 실행해줍니다. 관련 기능 관련 상세한 설명은 [링크](https://medium.com/prnd/github-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%84%B8%EC%A7%80%EC%97%90-jira-%EC%9D%B4%EC%8A%88%EB%B2%88%ED%98%B8-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EB%84%A3%EC%96%B4%EC%A3%BC%EA%B8%B0-779048784037)를 참고해주세요.

### 신규 기능 개발 
1. Github Projects에서 신규 이슈를 생성합니다.
2. [권장사항] `utils` 파일의 `ISSUE_ID_SEQ` 변수 값과 이슈 번호가 일치하는지 확인합니다.
3. `git checkout master` 명령어를 통해 master 브랜치에 이동한 후  `git fetch -p`로 신규 변경 사항을 원격으로부터 다운로드 받습니다.
4. `git merge  --ff-only origin/master`를 통해 HEAD를 이동합니다.
5. `create_branch {simple branch description}` 명령어를 통해 신규 브랜치에 체크아웃합니다.
6. 해당 브랜치에서 커밋할 경우 커밋 메시지에 `{PROJECT_NAME}-{ISSUE_ID_SEQ}` 형태로 prefix가 붙습니다.
7. 위의 내용은 `git log` 명령어를 통해 확인할 수 있습니다.

### 브랜치를 잘못 생성할 경우
1. `git branch -d {branch-to-delete}` 명령어를 통해 잘못 생성한 브랜치를 삭제합니다.
2. `utils` 파일에서 `ISSUE_ID_SEQ` 변수 값을 이전의 값으로 원상 복귀시켜줍니다.
3. `create_branch {simple branch description}` 명령어를 통해 다시 브랜치를 만들어 줍니다.
