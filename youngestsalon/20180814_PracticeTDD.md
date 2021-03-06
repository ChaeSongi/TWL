#### 2018.08.14 데잇걸즈 TWL : 프로그래밍 연습



- 피드백
  - 지난 수업 피드백
  - 국민청원 분류 제안 과제 피드백 
    - 유익한 중간 결과물 만들기
    - 선생님 : 좋은 분류 시스템을 공부 → 적절한 Hierarchy 설정



- F조 이터레이션 회의

  ~~~
  1. 지난주 작업 현황
  - 데이터 1차 수집/정리
  - Folium으로 지도 상에 구현 (롯데몰/스타필드)
  
  2. 이번주 목표
  - 기존 데이터(상점정보) 활용 (Word2Vec. WordCloud) : 지은님
  - 인스타그램 태그 크롤링, 시각화 : 지은님, 윤경님
  - 상관관계 분석, Folium 지도 상에 데이터 추가 : 송이님
  - 유동인구 정보 검색, 네이버 블로그 크롤링(VOC 체크 목적) : 은지
  
  3. 다음주 목표
  - 기존 데이터(멀티 타임라인) 활용
  - 기존 데이터(네이버 블로그 크롤링) 활용
  
  * 유동인구 정보 Plan B : 상권분석 서비스 정보 중 도로별 유동인구 정보로 추정
  (http://golmok.seoul.go.kr/sgmc/customanals/get_one_stop_trdar_cmpr.do?level1=3&level2=6&trdarCd=000247###)
  ~~~

  

- 나는 누구, 여기는 어디?

  - 웹 크롤링을 위한 Concept map

  ![Web Crawling의 Concept Map](https://github.com/YoungestSalon/TIL/blob/master/concept-map.JPG?raw=true)



- 프로젝트를 시작하는 방법들

  - 다른 사람의 소스 코드를 복제(Clone) 해서 시작
  - GitHub에 빈 Repository를 만들고 시작
  - 내 컴퓨터에서 시작 

  

- (실습) 프로그래밍 연습 : Vending Machine Bot ver.2

  - (참조) Git Bash 명령어

    ~~~
    1. cd : Change Directory
    2. mkdir : MaKE DIRectory
    3. pwd : 현재 작업 중인 디렉토리는 어디?
    4. ls : 폴더 안에 있는 파일들은?
    5. ls -a : 폴더 안에 있는 파일들은? (숨겨진 파일/폴더 포함)
    6. git init : git 폴더로 설정
    7. atom . : 현재 폴더를 Atom 편집기에서 Open
    8. touch (파일명) : 파일의 최종 수정일을 변경, (없는 파일명이면) 새로운 파일을 생성
    9. echo (파일 내용) > (파일명)
      - '파일 내용'을 집어넣은 파일을 새로운 파일로 생성
      - 파일명이 기존에 존재하는 파일인 경우, 기존 파일에 '파일 내용'을 덮어씀
      - Ex. echo Hello > test.txt : Hello라는 내용을 넣은 test.text 파일을 생성
    10. echo (파일 내용) >> (파일명)
      - 앞의 명령어와 동일
      - 단, 파일명이 기존에 존재하는 파일인 경우, 덮어쓰는 것이 아니라 추가함.
    11. git commit -am "메시지"
      - git add와 git commit을 동시에 처리해줌
      - 단, Untracked 상태의 파일은 commit 처리해주지 못함
    12. git commit -am -all "메시지"
      - git add와 git commit을 동시에 처리
      - Untracked 상태의 파일도 commit 처리해줄 수 있음
    ~~~

  - 실습 환경 Setting

    ~~~
    1. Git Bash : 폴더 생성, git init, 파일 생성
    2. Atom : 테스트 코드 파일 생성 (반드시 test_로 시작하는 이름으로 생성)
    3. Anaconda Prompt : 가상환경 생성, 단위테스트 라이브러리 설치, 테스트 코드 실행
       - 가상환경 생성 : pipenv --python 3.6
       - 단위테스트 라이브러리 설치 : pipenv install pytest
       - 테스트 코드 실행 : pipenv run pytest (성공하는지 확인 필요)
    4. Git Bash : 프로덕트 코드 파일 생성, '.gitignore' 파일 생성, git add/commit
    ~~~

  - Atom 꿀팁

    ~~~
    1. 동일한 단어를 동시에 수정하도록 선택하기 : Ctrl+D (Win) / Command+D (Mac)
    2. 여러 줄을 한꺼번에 주석 처리 : Ctrl + / (Win)
    3. 여러 줄을 한꺼번에 줄여쓰기 : Ctrl+C로 선택 후 Tab (Win)
    4. 저장 : Ctrl + S
    ~~~



- 테스트 주도 개발 (Test-Driven Development)

  - (복습) 테스트 주도 개발 순서

    1. 테스트 추가
    2. 테스트 실행 → 실패 확인
    3. 코드 수정 → 테스트 성공 확인
    4. 깔끔한 코드로 다듬기
       - 의도가 잘 드러나며, 중복이 없다.
       - DTSTTCPW : Do the simplest thing that could possibly work.
       - YAGNI : You ain't gonna need it
    5. 테스트 다시 실행 → 성공 확인
    6. Go to 1.

    

  - (시연) 테스트 주도 개발 사례 : 피보나치 수열 구현

    - 테스트 주도 개발의 '테스트' : 개발 알고리즘의 구현이 가능한 정도로 테스트 실행
    - 테스트 주도 개발을 해도 QA 과정은 필요 (테스트 대상, 범위, 방법이 다소 다름)

    

  - (실습) 테스트 주도 개발 사례 : Vending Machine Bot

    ~~~
    1. Atom : 테스트 코드 파일 생성
    2. Anaconda Prompt : 테스트 코드 실행, 에러 메시지 확인
    3. Atom : 에러 메시지를 참고하여 테스트 코드 파일 수정
    4. Anaconda Prompt : 테스트 코드 재실행, 성공 확인
    5. Atom : 깔끔한 코드로 다듬기
    6. Anaconda Prompt : 다듬은 코드에 대한 테스트 실행, 성공 확인
    7. Git Bash : git status, git idff, git add . , git commit
    ~~~

    

  - 좋은 테스트의 요건

    - Test Isolation : 테스트 간의 간섭 효과가 없어야 함

    - 하나의 기능(논리적인 단위) 별로 테스트가 생성되어야 함

      (= 오류는 1개인데 테스트 코드 여러 개가 깨진다면 테스트 코드를 잘못 짠거임)



- 클래스 도입하기

  ![인스턴스의 사례](https://github.com/YoungestSalon/TIL/blob/master/class_instance.JPG?raw=true)

  - 클래스(Class) : 범주		Ex. Integer
  - 인스턴스(Instance) 
    - 범주에 속한 사례. (= 객체. Object)		Ex. 1, 2, 3
    - 객체 = 내부의 상태(State) + 연산(Operations, Methods)
