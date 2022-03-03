

## 1. inner join
- default join 
- join 조건에서 동일한 값이 있는 행만 반환 

## 2. Natural Join 
- 두 테이블간의 join 조건에서 동일한 이름을 갖는 모든 칼럼들에 대해 join을 수행함.
- join되는 테이블의 데이터 도메인과 칼럼명, 칼럼값이 동일해야 join이 수행됨.
- 따라서 on 절이 없다. 
- Natural Join에서는 모든 일치되는 칼럼들에 대해 JOIN이 이루어지지만 from 절의 using 조건절을 이용하면 같은 이름을 가진 컬럼들 중 원하는 칼럼들에 대해 선택적으로 equi join을 할수있다.

## 3. Cross Join
- 테이블간 JOIN 조건이 없는 경우 생길 수 있는 모든 데이터의 조합. 
- 두 개 테이블의 결과는 양쪽 집합의 M*N 건의 데이터 조합이 발생.
