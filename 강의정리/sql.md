
## DBeaver 사용법
블럭 지정후 Ctrl + Enter -> 실행 
Ctrl + Shift + E -> 실행 계획을 볼 수 있다. (dbeaver만)

```sql
SELECT ---3
  FIRST_NAME ---4
FROM ---1
  CUSTOMER ---2
```

### ALIAS
SELECT * FROM CUSTOMER A 이렇게 쓰는거.
ALIAS를 쓰면 코드의 가독성이 좋아지고 SQL 성능이 좋아짐

### DBMS
DBMS에는 옵티마이저가 있다.
ALIAS를 쓰면 옵티마이저가 가장 가장 빠르게, 가장 저비용으로 SQL을 실행하는데 도움을 준다.

### COMMIT
COMMIT 명령어는 DDL에서는 수행되지 않음.
