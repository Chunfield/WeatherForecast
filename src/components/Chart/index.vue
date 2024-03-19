<template>
    <div class="green">
        <div class="charts" ref="chart"></div>
        <button @click="handleLeftButtonClick" class="ar">←</button>
    </div>
</template>

<script>
import * as echarts from 'echarts';
export default{
    data(){
        return{
            chart:'',
            temdata:[this.nextWeek[0]?.tem,this.nextWeek[1]?.tem,this.nextWeek[2]?.tem,this.nextWeek[3]?.tem,this.nextWeek[4]?.tem,this.nextWeek[5]?.tem,this.nextWeek[6]?.tem,],
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
    //             dataZoom: [  
    //     {  
    //         type: 'slider',   
    //         start: 10,  
    //         end: 60 
    //     },  
    //     {  
    //         type: 'inside', 
    //         start: 10,  
    //         end: 60  
    //     }  
    // ],
                tooltip: {  
                    trigger: 'item', 
                    axisPointer: {  
                    type: 'line'  
                                },
                        },  
    
                series: [{  
                    name: '温度',  
                    type: 'line',
                    smooth:'true',
                    symbol: 'circle',
                    symbolSize:9,
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
                    data: [this.temdata[0],this.temdata[1],this.temdata[2],this.temdata[3],this.temdata[4],this.temdata[5],this.temdata[6],]  
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
.green{
    background-color: green;
}
.ar{
    position: absolute;
    height: 50px;
    width: 50px;
}
</style>