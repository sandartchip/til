
- MySQL은 하나의 테이블에 최대 4096개의 컬럼을 가질 수 있음.
- row size는 65,535 byte로 제한되어 있다.
- 큰 varchar필드가 많은 테이블의 경우, row 사이즈 제한 때문에 다음과 같은 SQL에러가 난다.


### Text필드와 Varchar필드 
- TEXT : 길이를 설정하지 않으며, 속성의 최대 길이를 모를 때 사용함.


### 속도
- varchar의 조회 속도가 빨라서, varchar을 사용할 수 있을 때 text를 사용하지 않음.



