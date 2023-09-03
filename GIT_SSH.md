# GIT SSH 키생성

## SSH key
1. 생성 
  - 홈디렉토리(c:users/사용자이름/.ssh)에 `.ssh` 디렉 토리 생성 
  ```
    mkdir ~/.ssh
    cd ~/.ssh
  ```
  - `cd ~/.ssh` : ssh key 관리하는 디렉토리로 이동
  - `ls -al` or `ls -l`   : 기존 파일 목록 확인
  - 키생성 "id_userA" key파일 이름 : 기본값으로 생성 `ssh-keygen`
  ```
  ssh-keygen -t rsa -C "userA@example.com" -f "id_userA"
  ```
  - enter 치면 비밀번호 없이 사용할 수 있습니다.
  ```
  Enter passphrase (empty for no passphrase): 
  Enter same passphrase again: 
  ```
  - `.pub` 공개키고 없는것이 개인 키 입니다.


## SSH 키생성 
- `.ssh` 폴더 생성 위치
win : C:\Users\사용자\.ssh

  + 리눅스 명령   
  > cd ~                    : 홈디렉토리 이동  
  > mkdir ~/.ssh            : .ssh 폴더 생성  
  > chmod 700 ~/.ssh        : .ssh 폴더 권한 설정  
  > cd .ssh                 : .ssh 폴더 이동  
  > ssh-keygen -t rsa -b 4096 -C "email@example.com" : 키생성  
  > ls -l                   : 파일 리스트 보기  
  > cat ~/.ssh/id_rsa.pub   : id_rsa.pub 공개키 내용 출력  
  > eval $(ssh-agent -s)    : pid 번호 확인  
  > ssh-add ~/.ssh/id_rsa  : 개인키파일 사용하여 ssh-agent 등록 


- 폴더이동후 ssh키생성   
  "email@example.com"본인 이메일 주소 입력  

  + ssh 키등록 명령
  > ssh-keygen : ssh 비대칭키 생성 명령어    
  > -t rsa : 암호화 타입을 rsa 방식을 사용   
  > -b 4096 : 생성할 키의 비트수 4096으로 지정, rsa 타입을 위해선 최소 768 비트가 필요하며 default로 2048 비트이다. 4096으로 더 난독화된 키를 생성한다.    
  > -C “email@example.com“ : 코멘트로 일종의 주석이다. 보통 이메일 계정이나 아이디등을 입력한다.   
  > ssh-keygen : ssh 비대칭키 생성 명령어   
  > -t rsa : 암호화 타입을 rsa 방식을 사용  
  > -b 4096 : 생성할 키의 비트수 4096으로 지정, rsa 타입을 위해선 최소 768 비트가 필요하며 default로 2048 비트이다. 4096으로 더 난독화된 키를 생성한다.   
  > -C “email@example.com“ : 코멘트로 일종의 주석이다. 보통 이메일 계정이나 아이디등을 입력한다.

  ```
  ssh-keygen -t rsa -b 4096 -C "email@example.com"
  ```

- 비빌번호 입력, 한번더 입력
```
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\사용자/.ssh/id_rsa):

Enter passphrase (empty for no passphrase): 
Enter same passphrase again:
```
- id_rsa(개인키), id_rsa.pub(공개키) 

## GitHub 등록
- 공개키를 githug에 등록하기
  + `id_rsa.pub` 내용을 카피 
  + github 로그인후 계정 메뉴 > Settings > Account settings > SSH and GPG keys > New SSH key 버튼클릭 > Title:ssh설명, Key:id_rsa.pub 내용 > Add SSH key 버튼클릭
  
  
  