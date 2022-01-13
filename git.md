# Git

 Git: 분산 버전 관리 시스템 (분산된 버전 관리를 하는 시스템)

- 버전 관리
  - 코드의 히스토리(버전)을 관리하는 도구
  - 개발되어온 과정 파악 가능
  - 이전 버전과의 변경 사항 비교 및 분석
- 분산
  - 중앙 집중: database 1개 
  - 분산: database 여러 개
  - 깃은 변경 사항만을 저장: 편집, 복구 용이

- 버전관리를 하는 프로그램이 git, git으로 버전관리된 데이터를 저장하는 것이 github



- gitlab: server 자체(저장소)를 구축할 수 있게 해줌
- github: ms server에 데이터 저장



- git은 분산 버전 관리 시스템이며 github는 git 기반의 저장소 서비스 

  => git과 github는 다르다



- CLI <-> GUI
  - CLI 명령 줄 인터페이스
- Unix / Linux 명령어: 명령 프롬프트 X /powershell O
  - ls 현재 위치의 폴더, 파일 목록을 보여주는 명령어 / clear 목록을 다 지우는 명령어
  - (명령 프롬프트 dir - cls)
  - cd <path> 현재 위치 이동하기 (<path>에는 폴더 이름) / cd .. 상위 폴더로 이동 (한 칸 띄고 ..)
    - .. (한 칸 위) 부모 위치 의미
  - mkdir <name> 폴더 생성하기
    - 파일명이 길 경우 tab 누르면 폴더, 파일명이 나옴
  - touch <name> 파일 생성하기 -> powershell에서 지원 안 됨(git bash를 이용하자)
  - rm <name> 파일 제거하기 / rm -r <name> 폴더 제거하기 (r(recursive): 폴더 안 쪽에 있는 걸 모두 포함해서 지운다는 의미의 옵션)

- gitbash ~ : user의 home directory 
  - code . : 명령어를 친 위치에서 visual studio code 열림



- README.md: 프로젝트 설명서



- git init: 로컬 저장소 생성

- 특정 버전으로 남긴다 = "커밋(Commit)한다" 

- repository안에 commit이 점점 쌓여갈 것
- repository 안에 repository를 만들지 말 것! (만들 었을 경우 .git 폴더 지우기)



- Working Directory: 내가 작업하고 있는 실제 디렉토리
- Staging Area: 가상 공간. 커밋(commit)으로 **남기고 싶은**, 특정 버전으로 **관리하고 싶은** 파일이 있는 곳
- Repository: 커밋(commit)들이 저장되는 곳



- git add <name>
- git add .: 추적 되지 않은 모든 파일과 추적 하고 있는 파일 중 수정 된 파일을 '모두' (이전 사항과 비교해 변경 사항이 모두) staging area에 올라감  
  - .은 현재 위치라는 의미
- git status: 현재 git 으로 관리되고 있는 파일들의 상태를 알 수 있음

- git commit -m "commit-message" : 커밋 메세지는 자세하게, 구체적이게
- git config user.name "user_name": github 사용자 이름 등록
- git config user.email "user_email": github 사용자 이메일 등록
- END가 뜰 경우 q를 누르면 나가짐

- git log: git의 commit history 보기
- git diff (commit id 앞 네 자리) (commit id 앞 네 자리) : 두 commit 간 차이 보기, 앞 commit을 기준으로 뒤에 commit을 비교



local repository / remote repository(github ...)

- remote -> local: clone

  - clone: remote_repo를 local로 복사

  - push/pull: commit단계에서 변경 사항만 가져오는 것
    - 코드 수정은 github에서 하지 않고 local에서 수정해서 push/pull 할 것!



- local -> remote

  - git remote add origin {remote_repo_url.git}
    - remote_repo(github에서 생성한 repo 주소)를 origin(repo_name)으로 부를 것이라고 선언하는 것

  - git push -u origin master
    - -u: set-upstream. remote repository를 등록한 다음에만 쓰면 됨 local의 master를 origin(remote)으로 보낼 거라는 의미
    - master: local branch

  - git push origin master
    - local repo의 최신 커밋을 remote repo로 push

