feature - develpo - release - hotfixes - master 단계로 branch를 나눠서 코드를 관리하는 전략입니다.
이를 사용자가 쉽게 접근하고 사용할수 있도록 확장 기능(명령어)를 제공하는 것이 gitflow입니다.


Feature

1. git-flow-avh 설치 (brew install git-flow-avh)
2. 저장소 연결 (git remote add origin git@github.com:MaxNam/git-flow-test2.git)

- git checkout master
- git push origin master
- git push origin develop

3. develop 브런치에서 feature 브런치 생성 (git flow feature start login)
4. remote 저장소에 해당 feature 생성 (git flow feature publish login)
5. commit 이거저거 테스트
6. remote 저장소에 푸시 (git push origin login)
7. github pr날림 (open)
8. pr 확인이 끝났으면 feature 브런치 merge

- git flow finish -k

9. local에서 merge develop 푸시 => remote에 feature 삭제, pr close

- git push origin develop
- git flow feature finish login



Release

1. develop 브런치에서 release 브런치 생성 (git flow release start v.0.1)
2. remote 저장소에 해당 release 생성 (git flow release publish v.0.1)
5. commit 이거저거 테스트
3. remote 저장소에 푸시 (git push origin v.0.1)
4. github pr날림 (open)
5. pr 확인이 끝났으면 release 브런치 종료 (git flow release finish v.0.1) -> local feature은 merge되면서 삭제 -> 커밋 내용, tag 내용 저장..
6. local에서 merge develop 푸시 (git push origin develop) => remote에 release 삭제, pr close
7. tag 푸시 (git push --tags)

Hotfix

1. master 브런치에서 hotfix 브런치 생성 (git flow hotfix start v.0.1)
2. remote 저장소에 해당 feature 생성 (git flow feature publish v.0.1)
5. commit 이거저거 테스트
3. remote 저장소에 푸시 (git push origin v.0.1)
4. github pr날림 (open)
5. pr 확인이 끝났으면 feature 브런치 종료 (git flow feature finish v.0.1) -> local feature은 merge되면서 삭제 -> 커밋 내용, tag 내용 저장..
6. local에서 merge develop 푸시 (git push origin develop) => remote에 feature 삭제, pr close









1. Git flow command error: 'flow' is not a git command

 -> brew install git-flow-avh

2. Fatal: Not a gitflow-enabled repo yet. Please run 'git flow init' first

 -> git flow init -d

3. Fatal: Working tree contains unstaged changes Aborting

 -> git stash (임시저장)

4. git flow publish => commit을 허용


STEP

 1. git flow feature start f1
 2. git status
 3. git add .
 4. git commit -am 'add'

 5. git flow feature publish f1
 6. git push origin feature/f1
 7. github pull request
 8. git flow feature finish f1
 	- merge, delete feature/f1, switch develop
 9. git push origin develop



git 순서도

 - https://danielkummer.github.io/git-flow-cheatsheet/index.ko_KR.html
