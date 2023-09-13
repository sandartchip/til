

## 가로 그래프, 세로 그래프 

#### Vertical Graph (Default)
```javascript
var chart = echarts.init(document.getElementById('chart-container'));

var option = {
    xAxis: {
        type: 'category',
        data: ['Category A', 'Category B', 'Category C', 'Category D', 'Category E'],
    },
    yAxis: {
        type: 'value',
    },
    series: [{
        type: 'bar', // Use 'bar' type for vertical bars
        data: [80, 90, 70, 85, 95],
    }]
};

chart.setOption(option);
```

#### Horizontal Graph
```javascript
var chart = echarts.init(document.getElementById('chart-container'));

var option = {
    yAxis: { // Use yAxis for horizontal bars
        type: 'category', // Specify the type as 'category' for labels
        data: ['Category A', 'Category B', 'Category C', 'Category D', 'Category E'],
    },
    xAxis: { // Use xAxis for values
        type: 'value',
    },
    series: [{
        type: 'bar', // Use 'bar' type for horizontal bars
        data: [80, 90, 70, 85, 95],
    }]
};

chart.setOption(option);
```
