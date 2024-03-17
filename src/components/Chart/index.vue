<template>
    <div class="charts" ref="chart"></div>
</template>
<script>
import * as echarts from 'echarts';
export default{
    data(){
        return{
            chart:'',
        }
    },
    props:['weather-data','nowweatherData','currentweatherData','nextWeek'],

    mounted(){
        this.drawChart()
    },
    methods:{
       drawChart(){
        this.chart = echarts.init(this.$refs.chart);
            const option={
                title:{
                    text:"未来七天气温预报",
                    textStyle: {   
                    color: '#fff'   
                                }  
                },
                xAxis:{
                    type: 'category',
                    data:["今天","明天","后天",this.nextWeek[3]?.week,this.nextWeek[4]?.week,this.nextWeek[5]?.week,this.nextWeek[6]?.week],
                    boundaryGap:false,
                    axisLabel:{
                        align:'center',
                    },
                    axisLine:{
                        lineStyle:{
                            color:'#fff',
                        }
                    },
                },
                yAxis:{
                    type: 'value',
                    interval: 10,
                    splitLine:{
                        show:false,
                    },
                    axisLabel: {  
                        show: true,
                        fontSize:15,  
                        formatter: '{value} ℃'   
                    },
                    axisLine:{
                        lineStyle:{
                            color:'#fff',
                        }
                    }  
                },
                
                series: [{  
                    name: '气温图',  
                    type: 'line',
                    smooth:'true',
                    symbol: 'circle',
                    symbolSize:6,

                    areaStyle: {
                    color: 'rgba(64, 60, 60, 0.3)',
                    opacity: 0.5
                               },

                    itemStyle: {  
                    color: 'rgba(64, 60, 60, 0.3)',   
                    borderColor: '#fff',   
                    borderWidth:1   
                                },  
                    lineStyle:{
                        color: '#fff',
                        width:1
                    },
                    data: [this.nextWeek[0]?.tem,this.nextWeek[1]?.tem,this.nextWeek[2]?.tem,this.nextWeek[3]?.tem,this.nextWeek[4]?.tem,this.nextWeek[5]?.tem,this.nextWeek[6]?.tem,]  
                        }]  
            }
            this.chart.setOption(option);
       }
    }
}

</script>
<style>
.charts{
    height:250px;
    width: 100%;
}
</style>