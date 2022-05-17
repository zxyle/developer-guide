### 介绍

数据可视化库, https://echarts.apache.org/zh/index.html



### 安装

```bash
yarn add echarts
yarn add echarts-for-react
```



### 折线图示例

```jsx
import ReactEcharts from 'echarts-for-react';

let option = {
  xAxis: {
    type: 'category',
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
  },
  yAxis: {
    type: 'value'
  },
  series: [
    {
      data: [150, 230, 224, 218, 135, 147, 260],
      type: 'line'
    }
  ]
};

<ReactEcharts option={option} />
```

