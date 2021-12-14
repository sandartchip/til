

## DBeaver 사용법
블럭 지정후 Ctrl + Enter -> 실행 
Ctrl + Shift + E -> 실행 계획을 볼 수 있다. (dbeaver만)

```sql
SELECT ---3
  FIRST_NAME ---4
FROM ---1
  CUSTOMER ---2
```

### SELECT DISTINCT

```sql
SELECT DISTINCT COLUMN_1, COLUMN2 
FROM TABLE_NAME
```
=> COLUMN_1 + COLUMN_2의 중복 값 존재 시 중복값을 제거. 

### ALIAS

```sql
SELECT ---3
  A.FIRST_NAME ---4
FROM ---1
  CUSTOMER A---2
```
이렇게 쓰는거.
ALIAS를 쓰면 코드의 가독성이 좋아지고 SQL 성능이 좋아짐

### DBMS
DBMS에는 옵티마이저가 있다.
ALIAS를 쓰면 옵티마이저가 가장 가장 빠르게, 가장 저비용으로 SQL을 실행하는데 도움을 준다.

### COMMIT
COMMIT 명령어는 DDL에서는 수행되지 않음.


### Intersect

두 쿼리의 교집합을 구하는 방법. JOIN 방식이 더 성능이 좋음


### Except 
- 실무에서 많이 쓰임
 
