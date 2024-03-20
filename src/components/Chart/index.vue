<template>
    <div class="green">
        <div class="charts" ref="chart"></div>
        <button @click="zoomLeft" class="ar1">&lt;</button>
        <button @click="zoomRight" class="ar2">&gt;</button>
    </div>
</template>

<script>
import * as echarts from 'echarts';
export default{
    data(){
        return{
            chart:'',
            dataZoom: {  
                start: 10,  
                end: 70  
                    },
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
                                },
                    top:'10px'  
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
              
                tooltip: {  
                    trigger: 'item', 
                    axisPointer: {  
                    type: 'line'  
                                },
                    backgroundColor:'rgba(64, 60, 60, 0.1)',
                    textStyle:{
                        color:'#fff'
                              },       
                    },
                       
                        dataZoom: [  
                        {
                        show:false,  
                        start: this.dataZoom.start,  
                        end: this.dataZoom.end,  
                        }  
                                    ], 
    
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
       },
       zoomLeft() {  
      
      if (this.dataZoom.start > 0) {  
        this.dataZoom.start -= 10;  
        this.dataZoom.end -= 10;  
        this.updateChart();  
      }
    },

      zoomRight() {    
      if (this.dataZoom.end < 100) {  
        this.dataZoom.start += 10;  
        this.dataZoom.end += 10;  
        this.updateChart();  
      }  
    },

    updateChart() {  
      this.chart.setOption({  
        dataZoom: [{  
          start: this.dataZoom.start,  
          end: this.dataZoom.end  
            }]  
        });  
        },    
    }
}


</script>
<style>
.charts{
    height:250px;
    width: 85%;
    margin: 0 auto;
}
.green{
    position: relative;
    background-color: rgba(240, 236, 236, 0.056);
    border-radius: 10px;
}
.ar1{
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: transparent;
    border: none;
    font-size: 32px;
    color: aliceblue;
}
.ar2{
    position: absolute;
    top: 50%;
    right: 0;
    transform: translateY(-50%);
    background-color: transparent;
    border: none;
    font-size: 32px;
    color: aliceblue;
}
</style>