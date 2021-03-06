#### 2018.08.09 데잇걸즈 TWL : 테스트 주도 개발



1. ##### 오전 : 테스트 주도 개발 (애란쌤)

- 피드백의 피드백 

- 정규표현식 과제 피드백

  - Stepwise refinement : 문제를 작은 단위로 나눠서 글로 적은 후 접근하는 방법

    

- (실습) Slackbot : Vending Machine bot 만들기

  ~~~
  - 'Slackbot' Repository Fork (@Web) → Local PC로 Clone (@Git Bash)
  - @Anaconda Prompt : Clone한 폴더로 이동 → 가상환경 설정(pipenv install)
  - @Atom : Token 정보 입력 (secret.py), 호출어/답변 변경 (main.py)  
  - @Git Bash : Add / Commit / Push 
  - @Anaconda Prompt : Main.py 실행 (pipenv run python main.py)
  ~~~

  

- (실습) 자동화 된 단위 테스트 만들기 : [GitHub 코드](https://github.com/YoungestSalon/slackbot) 참조

  ~~~
  - @Atom : Slack과 통신하는 부분, 호출/답변 대화 로직 부분을 분리하고 코드를 정리
  - @Anaconda Prompt : Main.py 종료(Ctrl + C) & 재시작
  - @Slack : 새로 설정한 대화 로직이 작동하는지 체크
  - @Git Bash : Add / Commit / Push
  - @Atom : 대화 로직 부분 파일 분리(chatlogic.py), Chatlogic import 코드 삽입 (Main.py)
  - @Anaconda Prompt : pip install pytest 실행
    - pytest : 자동화 된 단위 테스트를 만들어 줌
  - @Atom : pytest 코드 추가 (Packages 내 pytest = "*" 추가. @Pipfile)
  - @Atom : 단위 테스트용 코드 생성 (tests.py)
  - @Anaconda Prompt : pipenv run pytest tests.py 로 단위 테스트 실행
  ~~~

  - 장점 : Slack이나 Main.py (@Anaconda prompt) 의 재부팅/실행 없이 테스트가 가능

  - 테스트 자동화 코드를 짜기 어려울만큼 로직 코드가 복잡하면, 로직 코드 단순화가 선행과제임.

    

- 테스트 주도 개발 (Test-driven development)

  - 先 개발 後 테스트가 아니라, 先 테스트 後 개발의 관점

  - 이터레이션, 일일 회의/회고, 짝 프로그래밍 등과 함께애자일 방법론의 실천법 중 하나임

  - 순서

    1. 테스트를 추가한다.

    2. 테스트를 실행하여 테스트 실패를 확인한다.

       - 실패(fail) : 의도했던 테스트를 아예 실행조차 못 해 본 상태
       - 테스트 실패(error) : 의도했던 테스트를 실행했는데 expected 결과값이 안 나온 경우

    3. 코드를 고쳐서 최대한 빨리 테스트를 성공시킨다.

    4. 코드를 깔끔하게 다듬는다.

       - 리팩토링 (refactoring) : 프로그램 동작은 유지하며 설계를 개선. 책 [리팩토링](http://www.hanbit.co.kr/store/books/look.php?p_code=B9939119873) 참조.

       - 깔끔한 코드 (clean code) : 의도가 잘 드러남, 중복이 없음.
       - 좋은 코드 : Clean Code that works (작동함, 깔끔한 코드임)

    5. 테스트를 다시 실행하여 여전히 성공하는지 확인한다.

    6. Go to Step 1





2. ##### 오후 : 상권 분석하기 (배로쌤)

- Matplotlib의 그래프 한글 폰트 설정 박제하기

  - matplotlib의 설치 위치 / 설정 파일 위치 확인

    ~~~
    print ('버전: ', mpl.__version__)
    print ('설치 위치: ', mpl.__file__)
    print ('설정 위치: ', mpl.get_configdir())
    print ('캐시 위치: ', mpl.get_cachedir())
    print ('설정파일 위치: ', mpl.matplotlib_fname())
    ~~~

  - Atom에서 matplotlib 설정 파일을 open file 해서 font.family 를 변경

  - 설치된 폰트 테스트

    ~~~
    import pandas as pd
    import numpy as np
    from plotnine import *
    
    n = 10
    df = pd.DataFrame({'x축': np.arange(n),
                       'y축': np.arange(n),
                       'yfit': np.arange(n) + np.tile([-.2, .2], n//2),
                       '고양이': ['냐옹', '나비']*(n//2)})
    
    (ggplot(df)
     + geom_col(aes('x축', 'y축', fill='고양이'))
     + geom_point(aes('x축', y='yfit', color='고양이'))
     + geom_path(aes('x축', y='yfit', color='고양이'))
     + theme(text=element_text(family='NanumBarunGothic'))
    )
    ~~~

    

- (실습) 상권분석

  - 자료 출처 : [공공데이터포털 상가(상권)정보](https://www.data.go.kr/dataset/15012005/fileData.do)

  - GitHub Repository 및 Local 작업용 폴더 생성 : .gitignore 파일도 추가 생성

    ~~~
    # .gitignore 파일 코드
    
    .ipynb_checkpoints/
    .csv
    .tsv
    .zip
    ~~~

  - Jupyter Notebook 환경에서 상권 분석 실습 후 결과물을 GitHub에 Add / Commit / Push
