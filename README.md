# git-study
git를 익히기 위한 연습용 디렉토리

Git이란 source 관리를 위한 분산 버전 관리 시스템으로 최초로 리눅스 토발즈가 리눅스 커널 개발에 이용하려고 개발했다.  

![image](https://user-images.githubusercontent.com/79975172/124390198-6ef4d680-dd25-11eb-8470-5f9a2ad056b3.png)

Git은 파일을 Commited , Modifed, Staged 세가지 상태로 관리한다.  
commited : 데이터가 로컬저장소에 안전하게 저장됐음을 의미  
modified : 수정한 파일을 아직 로컬 저장소에 commit하지 않은 것을 의미  
staged : 현재 수정한 파일을 곧 Commit할 것이라고 표시한 상태를 의미  

Git은 Git Directory, Working Directory, Staging Area 세가지 영역으로 구분한다.  
Git Directory : Git이 프로젝트의 메타데이터와 객체 데이터베이스를 저장하는 곳  
Working Directory : 수정할 파일들이 있는 디렉토리  
Staging Area : Git Directory 에 있으며, 단순한 파일이고 곧 commit할 파일에 대한 정보를 저장한다.  

Working Directory의 모든 파일은 Tracked와 Untracked로 나뉜다.  
Tracked 파일은 Unmodified, Modified, Staged 상태중 하나의 상태를 갖는다.  
Tracked 파일이 아닌 파일은 Untracked 파일이다.  

Git에서 branch는 커밋 사이를 가볍게 이동할 수 있는 포인터 같은 것이다.  
git은 기본적으로 master 브랜치를 만든다. Git은 최초로 커심하면 master라는 이름의 브랜치를 만들고, 자동으로 master 브랜치가 가장 마지막 커밋을 가리킨다.  
  
Git은 HEAD라는 특수한 포인터를 갖고 있다. 이 포인터는 지금 작업하고 있는 로컬 브랜치를 가리킨다. "git branch <branch명>" 명령은 브랜치를 만들기만하고 브랜치를 옮기지는 않는다.  
"git checkout <branch명>" 명령으로 HEAD가 가리키는 브랜치로 이동할 수 있다.  
  
## command
gitconfig --global user.name <user명>  
초기 환경 설정 명령으로, 작업자의 이름을 설정하는 명령어이다.  
  
gitconfig --global user.email <email명>  
초기 환경 설정 명령으로, 작업자의 이메일을 설정하는 명령어이다.  
  
git init  
해당 디렉토리에 .git 디렉토리를 생성한다. 이 디렉토리는 git이 버전관리를 하기 위한 메타 정보를 담고있다.  

git remote add origin <github 디렉토리 http 주소>   
원격 저장소를 추가하는 명령어이다.  
   
git add .  
현재 디렉토리에 있는 모든 파일 및 디렉토리를 staged 상태(현재 수정한 파일을 곧 Commit할 것이라고 표시한 상태)로 만든다.  
  
git add <파일명.확장자>  
특정 파일을 tracked file로 만드는 명령어이다.
  
git rm --cached <파일명.확장자>  
tracked 파일을 Untracked 파일로 만드는 명령어이다.  
  
git commit -m "<message입력>"  
staged 파일들을 commit 한다. 반드시 해야하는 과정이다.  

git log  
commit 목록을 출력하는 명령어이다.  
   
git push origin master  
master 브랜치에 push 하는 명령어이다. 
  
git branch <branch명>   
branch 생성하는 명령어이다.  
  
git branch -b <branch명>  
branch 생성과 동시에 생성 branch 로 이동하는 명령어이다.  
  
git branch -d <branch명>  
branch를 삭제하는 명령어이다.  
  
git branch -r  
원격 branch를 출력하는 명령어이다.  
  
git branch -a  
원격 및 로컬 branch를 출력하는 명령어이다.  
  
git merge <branch명>  
현재 브랜치와 <branch명>을 merge 하는 명령어이다.

## push가 안되는 경우
![image](https://user-images.githubusercontent.com/79975172/124391320-09a3e400-dd2b-11eb-86b5-63e1c31f46dc.png)  
이렇게 뜨는 경우 push전에 pull을 해서 프로젝트를 병합해야한다.

pull 명령 실행시 "refusing to merge unrelated histories" 라는 문구가 나오면  
git pull origin <브랜치명> --allow-unrelated-histories
명령을 입력한다. 
git은 관련기록이 없는 두 프로젝트트를 거부하도록 되어있는데 이를 허용하도록 하는 옵션이 --allow-unrelated-hisotries 이다.

## pull 덮어쓰기
깃에 있는 파일을 로컬 저장소에 덮어쓰기 하고자 하는 경우  
git fetch --all   
git pull 받을 목록을 repository에서 업데이트  
  
git reset --hard origin/master  
git reset으로 head를 최신으로 가리킨다.    
  
git pull  
