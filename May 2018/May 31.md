## git 기본 명령어  

git config --global user.name "이름"
git config --global user.email "깃허브 메일주소" // 매번 물어보는 귀찮음을 피하기 위해 설정.

mkdir ~/MyProject   // 로컬 디렉토리 만들고  
cd ~/myproject      // 디렉토리로 들어가서  
git init            // 깃 명령어를 사용할 수 있는 디렉토리로 만든다.  
git status          // 현재 상태를 훑어보고  
git add 화일명.확장자  // 깃 주목 리스트에 화일을 추가하고 or  
git add .           // 이 명령은 현재 디렉토리의 모든 화일을 추가할 수 있다.  
git commit -m “현재형으로 설명” // 커밋해서 스냅샷을 찍는다.

git remote add origin https://github.com/username/myproject.git // 로컬과 원격 저장소를 연결한다.  
git remote -v // 연결상태를 확인한다.  
git push origin master // 깃허브로 푸시한다.

Bash에서 위와 같은 조작을 실행한 뒤 TIL 저장소를 연결함. Visual Studio Code를 이용해 편집 연결 적용  
Github Desktop도 설치했지만 VSCode를 많이 쓸듯  
월마다 폴더를 생성해 md 파일로 그 날의 TIL 저장

이따가 따로 파일 만들어서 정리해야겠다  
참고 출처 : https://gist.github.com/ninanung

# Python

## 22 - 19. Quiz: Circular Definitions

```
def popularity (p):
    score = 0
    for f in friends(p):
        score = score + popularity(f)
    return score
```
Would this definition work?  
(if p=='Alice': return 1)

1. Only if everyone is friends with 'Alice'.  
모두가 연결될 경우 무한 순환 고리에 빠지게 됨.

2. Only if no one is friends with 'Alice'.  
Alice를 제외한 나머지 친구들이 서로 연결되어 있으면 여전히 같은 문제가 발생.

3. Only if there is a friendship path from everyone to 'Alice'.  
마찬가지의 문제 발생.

4. Only if there are no cycles in the graph.  
코드에 친구가 없을 경우 함수를 끝내는 부분이 없으므로 끝나지 않음.

5. No.  
no u

## 20. Quiz: Relaxation

```
def popularity(t,p):
    if t == 0:
        return 1
    else:
        score = 0
        for f in friends(p):
            score = score + popularity(t-1,f)
        return score
```

Is this a good recursive definition?  
Yes.

새로운 값 t가 추가됨으로 인해 우리는 재귀함수의 종착점을 설정할 수 있다. 

---
# Summary

오늘은 GitHub 사용법과 다양한 기초 세팅으로 인해 Python 공부에 많은 시간을 쏟지 못했지만, 무언가 프로그래머가 되어가는 과정 중 기억할 만한 날이 될 것이다. 그 전에 GitHub은 그냥 osu! Spotlight Team에서 맵에 대한 평가를 쓴 뒤 최종 merge 전 미리 검토하는 용도로 쓰였는데, 이제 내 스스로의 연구실에 commit하고 다양한 자료를 넣는다고 생각하니 내심 뿌듯하기도 하다 ㅎㅅㅎ  
잘해보자 다들! 