<template>
    <div id="chart1" :style="{'width':widths+'px','height':heights+'px'}"></div>
</template>

<script>
import { onMounted, watch } from '@vue/runtime-core';
import *as echarts from 'echarts';
export default {
    name:'chart1',
    props:{
        widths:Number,
        heights:Number,
        chart_elem:Array,
        chart_val:Array,
        title:String,
        TypeofValue:Array,
        line_or_bar:Boolean
    },
    setup(props,context){
        var charttype=props.line_or_bar?'line':'bar';
        var SeriesInfo=[];
        for (let index = 0; index < props.TypeofValue.length; index++) {
            SeriesInfo.push({name:props.TypeofValue[index],
                type:charttype,
                data:props.chart_val[index]})
            
        }
        var option = {
            title: {
                text: props.title
            },
            tooltip: {},
            legend: {
                data:props.TypeofValue
            },
            xAxis: {
                data:props.chart_elem
            },
            yAxis: {},
            series:SeriesInfo
        };
        onMounted(function(){
            var mychart=echarts.init(document.getElementById("chart1"));
            mychart.setOption(option);
        })

    }
}
</script>

<style scoped>
    #chart1{
        margin: auto;
    }
</style>