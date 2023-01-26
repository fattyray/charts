<template>
  <h2>第一个组件可以根据所绑定的参数进行一个折线图或者是柱形图的绘制</h2>
  
<chart1 :widths="600" :heights="500" 
  :chart_elem="['一月','二月','三月','四月','五月','六月']" 
  :chart_val="[[300,400,100,200,120,600],[100,200,300,140,220,200]]" 
  :title="''" 
  :TypeofValue="['a销量','b销量']"
  :line_or_bar="true"></chart1>
  <h2> 第二个组件可以根据所绑定的参数进行一个饼状图的绘制</h2>

<chart2 :widths="600" 
:heights="400"
:chart_elem="['搜狗','百度','雅虎','谷歌','必应']"
:chart_val="[300,120,220,500,260]"
:title="'搜索引擎的使用比例'"
></chart2>
<h2>第三个组件可以根据提供的参数绘制一个雷达图</h2>

<chart3 
:widths="600" 
:heights="600"
:IndicatorName="['Sales','Administration','Information Technology','Customer Support','Development','Marketing']"
:Indicatormax="[6500,16000,30000,38000,55000,30000]"
:TypeofValue="['Allocated Budget', 'Actual Spending']"
:IndicatorValue="[[4200, 3000, 20000, 35000, 50000, 18000],[5000, 14000, 28000, 26000, 42000, 21000]]"
></chart3>
</template>
<script>
import HelloWorld from './components/HelloWorld.vue'
import chart1 from './components/chart1.vue';
import chart2 from './components/chart2.vue';
import chart3 from './components/chart3.vue';

export default {
  name: 'App',
  components: {
    chart1,
    chart2,
    chart3
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
