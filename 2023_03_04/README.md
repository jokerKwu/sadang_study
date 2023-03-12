### 문제 링크

1. 키로거
   https://www.acmicpc.net/problem/5397
2. 자동차 대여 기록에서 대여중 / 대여 가능 여부 구분하기
   https://school.programmers.co.kr/learn/courses/30/lessons/157340
3. 평균 일일 대여 요금 구하기
   https://school.programmers.co.kr/learn/courses/30/lessons/151136

### 상세 정보
소요 시간 :  60분
문제 해결 : ( 2 / 3 )    
해결 방법 :
-------

1. 키로거

스택을 활용하여 문제 해결
answer = [] 
stk = []
시뮬레이션 풀듯이 해당 문자마다 액션을 취한다.
- "<"  : 커서를 왼쪽으로 이동하므로 answer에 맨 마지막 문자를 stk에 푸시한다.
- ">"  : 커서를 오른쪽으로 이동하므로 stk에 맨 마지막 문자를 answer에 푸시한다.
- "-"  : 커서 앞 문자를 제거해야 되므로 answer에 맨 마지막 문자를 제거한다.

마지막으로 stk에 남아있는 문자들을 answer에 푸시하면 된다.

-------

2. 자동차 대여 기록에서 대여중 / 대여 가능 여부 구분하기

With 절을 사용하여 가상 테이블을 만든다.
가상 테이블에는 22년 10월 16일에 대여 중인 차에 대해서 AVAILABILITY 컬럼을 새로 만들어서 "대여중" 값을 넣는다.

기존 테이블과 가상 테이블을 car_id로 left join을 하고 group 으로 car_id를 묶는다.
그리고 AVAILABILITY 값이 비어있는 car_id에 대해서는 "대여 가능" 으로 값을 매긴다.

-------

3. 평균 일일 대여 요금 구하기

ROUND() 와 AVG() 내장 함수를 사용하여 쉽게 문제를 해결할 수 있다.

### 시행 착오

1. 키로거

시간 초과 때문에 애먹었다.

del 사용하게 되면 시간복잡도가 O(N) 이다.
arr.extend() 시간 복잡도 O(arr) arr 길이에 따라서 시간복잡도가 결정된다.
reversed() 시간 복잡도 O(N) 이다.

마지막에 stk에 남아있는 문자들을 answer에 옮기는 과정에서 for문을 사용하여 옮기면서 시간초과가 발생했다.
for문을 사용하지 않고 해결하는 방향으로 접근해서 해결했다.