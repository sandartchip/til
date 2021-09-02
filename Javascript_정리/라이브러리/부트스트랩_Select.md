
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
        console.log("클릭된 위치", this.options[this.selectedIndex].value);
        var species_url ="/soyeon_pj/sample/wgs/"+clicked_idx + "/sample_list/";
        location.href = species_url;
    });
```

