<template>
    <div id="chart3" :style="{'width':widths+'px','height':heights+'px'}"></div>
</template>

<script>
import { onMounted } from '@vue/runtime-core';
import *as echarts from 'echarts';
export default {
    name:'chart3',
    props:{
        widths:Number,
        heights:Number,
        IndicatorName:Array,
        Indicatormax:Array,
        TypeofValue:Array,
        IndicatorValue:Array

    
    },
    setup(props,context){
       var indicators=[];
       var seriesvalue=[];
       var types='radar';
       for (let index = 0; index < props.IndicatorName.length; index++) {
        indicators.push({name:props.IndicatorName[index],max:props.Indicatormax[index]})
        
       }
       for (let index = 0; index < props.TypeofValue.length; index++) {
        seriesvalue.push({name:props.TypeofValue[index],value:props.IndicatorValue[index]});
       }
       console.log(seriesvalue)
        var  option3 = {
  title: {
    text: 'Basic Radar Chart'
  },
  legend: {
    data: props.TypeofValue
  },
  radar: {
    // shape: 'circle',
    indicator: indicators
  },
  series:[{
    name:'Budget vs spending',
    type:types,
    data:seriesvalue
  }]
};
        onMounted(function(){
            var mychart=echarts.init(document.getElementById("chart3"));
            mychart.setOption(option3);
        })
    }
}
</script>

<style scoped>
    #chart3{
        margin: auto;
    }
</style>