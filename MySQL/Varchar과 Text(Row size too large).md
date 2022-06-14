
- MySQL은 하나의 테이블에 최대 4096개의 컬럼을 가질 수 있음.
- row size는 65,535 byte로 제한되어 있다.
- 큰 varchar필드가 많은 테이블의 경우, row 사이즈 제한 때문에 다음과 같은 SQL에러가 난다.

### Varchar
- variable max size of M characters
- M needs to be between 1 and 65535 takes 1 + c bytes (for M ≤ 255) or 2 + c (for 256 ≤ M ≤ 65535) bytes of disk space where c is the length of the stored string
can be part of an index

### Text필드
- TEXT : 길이를 설정하지 않으며, 속성의 최대 길이를 모를 때 사용함.
- fixed max size of 65535 characters (you cannot limit the max size)
takes 2 + c bytes of disk space, where c is the length of the stored string.
cannot be (fully) part of an index. One would need to specify a prefix length.


### 속도
- varchar의 조회 속도가 빨라서, varchar을 사용할 수 있을 때 text를 사용하지 않음.



