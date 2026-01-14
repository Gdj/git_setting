# git 

## 초기 설정
### commit
- 저장소 생성후 초기 커빗 (프로젝트 폴더 생성후)
```bash
  echo "# TR-stocks_favorites" >> README.md 
  git init 
  git add README.md 
  git commit -m "first commit" 
  git branch -M main
  git remote add origin https://github.com/Gdj/xxx.git  
  git push -u origin main
```

### clone
- 저장소내용 복제해 로컬에 받기
``` bash
  git clone https://github.com/Gdj/xxx.git
```

### push 
- 기존 저장소에 푸시
```bash 
  git commit -am "커밋 내용"  
  git push -u origin main
```

### pull
- 저장소 파일 받기 
```bash
  git pull
```
- 브런치이름 으로 받기
```bash
  git pull origin {이름}
```


### branch
- 현재 가지
```bash
  git branch
```
- 가지 만들기
```bash
  git branch {가지이름}
```
- 가지 이동
```bash
  git checkout {가지이름}
```
- 가지 만들고 이동
```bash
  git checkout -b {가지이름}
```