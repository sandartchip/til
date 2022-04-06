## client side & server side?
- serverside와 동시에 안되는건 -> 하나의 동작에 대해서 안되는거임. 
- search 자체를 serverside와 client side에서 동시에 수행할 수 없는 것.
- 반면에 search해서 이미 테이블에 렌더링된 결과를 client side로 재필터링하는건 가능.

![image](https://user-images.githubusercontent.com/15938354/136945410-2d35c332-05e6-45a3-8302-204ed542f2e5.png)

공식 문서 : https://datatables.net/manual/server-side


## columnDefs, render 할 때 row의 사용 
- 각 컬럼별로 넘어온  row 의 특정 값 렌더링 시킬 필요 있을 때 
 
```javascript 
    var columnDefs = [
        {
        "targets" : 4,
        "orderable" : false,
        "render" : function(data, type, row, meta) {
            console.log(row);
            var detail_html = "";
            
            detail_html += "<a href='/soyeon_pj/show_detail_result/" + row["result_folder_name"] + "/NONE/Dynamic/'>CLICK</a>";

            return detail_html;
        }
      }
```
## row 출력 결과 
![image](https://user-images.githubusercontent.com/15938354/136940953-79842f0c-b880-4e6a-83fd-647c3c8b0ad1.png)


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

https://zamezzz.tistory.com/310
