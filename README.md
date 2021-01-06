# Yootaek.Git.Command
Commands frequently used

## Submodule
### 서브모듈을 포함한 프로젝트 Clone
```bash
$ git submodule init // 서브모듈 정보를 기반으로 로컬 환경설정 파일이 준비된다.

$ git submodule update // 서브모듈의 원격 저장소에서 데이터를 가져오고 서브모듈을 포함한 프로젝트의 현재 스냅샷에서 Checkout해야 할 커밋 정보를 가져와서 서브모듈 프로젝트에 대한 Checkout을 한다.

$ git clone --recurse-submodules https://github.com/myProject // Clone 시 서브모듈을 자동으로 초기화하고 업데이트
```

### 서브모듈을 최신으로 업데이트
```bash
$ git fetch // 서브모듈 디렉토리에서 실행

$ git submodule update --remote // 상위 디렉토리에서 서브모듈 프로젝트를 Fetch하고 업데이트
```

### 서브모듈 추가하기
```bash
$ git submodule add https://github.com/myProject
```

### 서브모듈 관리하기
``` bash
$ git checkout [로컬 branch 명] // 서브모듈 수정사항을 추적하려면 Checkout이 필요하다.

$ git submodule update --remote // 서브모듈 수정 후 Upstream에서 서브모듈의 새로운 커밋을 가져온다. 
--rebase 나 --merge 옵션을 지정하지 않으면 Git은 로컬 변경사항을 무시하고 서버로부터 받은 해당 서브모듈의 버전으로 Reset하고 Detached HEAD 상태로 만든다.

$ git submodule update --remote --merge // --merge 옵션을 추가하면 서브모듈의 변경사항을 Merge 한다.

$ git submodule update --remote --rebase // --rebase 옵션을 추가하면 서브모듈의 변경사항을 rebase 한다.
```

### 서브모듈 수정 사항 공유하기
```bash
$ git push --recurse-submodules=check // 메인 프로젝트를 Push 하기 전에 서브모듈을 모두 Push 했는지 검사

$ git push --recurse-submodules=on-demand // 메인 프로젝트를 Push 하기 전에 서브모듈을 자동으로 푸시함

$ git config push.recurseSubmodules check[on-demand] // 위의 옵션이 항상 적용되도록 설정함
```

### Foreach 사용하기
foreach 명령을 이용하여 각 서브모듈에 같은 명령을 수행할 수 있다.
```bash
$ git submodule foreach "git status" // 서브모듈들의 git 상태를 가져온다.

$ git submodule foreach "git checkout master" // 각 서브모듈에서 로컬 master 브런치로 체크아웃한다.
```
