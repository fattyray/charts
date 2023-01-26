<template>
    <div id="chart2" :style="{'width':widths+'px','height':heights+'px'}"></div>
</template>

<script>
import { onMounted } from '@vue/runtime-core';
import *as echarts from 'echarts'; 
export default {
    name:'chart2',
    props:{
        widths:Number,
        heights:Number,
        chart_elem:Array,
        chart_val:Array,
        title:String
    },
    setup(props,context){
        var datas=[]
        for(let i=0;i<props.chart_val.length;i++)
        {
            datas.push({value:props.chart_val[i], name:props.chart_elem[i]})
        }
        var  option1 ={
  title:{
    text:props.title
  },
  tooltip: {
    trigger: 'item'
  },
  legend: {
    top: '5%',
    left: 'center'
  },
  series: [
    {
      name: '',
      type: 'pie',
      radius: ['40%', '70%'],
      avoidLabelOverlap: false,
      label: {
        show: false,
        position: 'center'
      },
      emphasis: {
        label: {
          show: true,
          fontSize: 40,
          fontWeight: 'bold'
        }
      },
      labelLine: {
        show: false
      },
      data:datas 
    }
  ]
};
        onMounted(function(){
            var mychart=echarts.init(document.getElementById("chart2"));
            mychart.setOption(option1);
        })
        
    }
}
</script>

<style scoped>
    #chart2{
        margin: auto;
    }
</style>