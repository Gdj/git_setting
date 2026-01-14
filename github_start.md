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
- 
``` bash
  git clone https://github.com/Gdj/xxx.git
```

### push 
- 기존 저장소에 푸시
```bash 
  git add .
  git commit -m "커밋 내용"
  git remote add origin https://github.com/Gdj/xxx.git
  git branch -M main 
  git push -u origin main
```