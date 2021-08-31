# 컬럼명
- 현재 html상의 컬럼 명으로 필터 검.
- html(javascript상의 컬럼명, 테이블의 스키마 일치 해야 함) => 맞나..

## render 함수
 
#### function render( data, type, row, meta )

### Description:
- If a function is given, it will be **executed whenever DataTables needs to get the data for a cell in the column. ** 
- 이 함수가 있으면, 이건 실행될 것이다. 데이터 테이블이, 각 컬럼의 셀들의 데이터를 필요로 할 때 마다. 
 
- Note that this function might be called multiple times, as DataTables will call it for the different data types that it needs - sorting, filtering and display.

- 데이터 테이블이 sort, filtering, display 등 다른 동작을 할 때마다, 이 함수는 여러 번 실행될 수 있다.

### Parameters:

- data: data for the cell 
- typethe 
