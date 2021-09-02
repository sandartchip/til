
# Select

```html
    <select class="custom-select" id="friend_select">
        <option selected>Select Friend</option>
        <option value="1">Minsus</option>
        <option value="2">JENNI</option>
    </select>
```

```javascript

    $("#species_select").on('change', function(e){ // SELECT 자체에 클릭 이벤트 건다 => 이벤트 delegation?
        clicked_idx = this.options[this.selectedIndex].value;
        
        console.log("이벤트 발생한 요소", e.currentTarget);
        console.log("클릭된 요소", e.target);

        console.log("클릭된 위치", this.options[this.selectedIndex].value);
        var species_url ="/soyeon_pj/sample/wgs/"+clicked_idx + "/sample_list/";
        location.href = species_url;
    });
```


![image](https://user-images.githubusercontent.com/15938354/131792594-7e6f94d3-7469-4c69-91e6-85a624405f45.png)

# 결론
- 클릭된 옵션 요소와 이벤트 발생한 요소가 다를 거라 예상, event delegation발생한 줄 알았는데 아님.
- 클릭된 요소도 select 전체 객체, 이벤트 발생도 select 전체 객체임. 
- 대신, 클릭된 위치를 알 수 있는 **select.selectedIndex**라는 select의 property(?)가 있음.



