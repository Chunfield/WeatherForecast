<template>
    <div class="box1">
        <div class="box1-bar1">
            <div class="Lbar1">
            <span class="bar1-city">{{ weatherData.city}}&nbsp&nbsp</span>
            <span class="bar1-tem">今天：{{weatherData.wea}}&nbsp&nbsp{{ weatherData.tem2 }}~{{weatherData.tem1}}℃&nbsp&nbsp</span>
            <div class="bar1-wind">{{ weatherData.win }}{{ weatherData.win_speed }}</div>
            <div class="bar1-hum"></div>
            </div>
         <div class="Lbar1">
            <div class="bar1-date">{{ weatherData.date }}&nbsp&nbsp</div>
            <div class="bar1-week">{{ weatherData.week }}</div>
            <div class="bar1-lunar"></div>
            </div>
        </div>
        <div class="box1-bar2">
            <div class="bar2-tem">{{ weatherData.tem }}℃</div>
            <div class="bar2-otem">
                <div class="bar2-air">
                    空气质量：{{ weatherData.air }}
                </div>
                <div class="bar2-others">
                    <div class="bar2-weather">{{ weatherData.wea }}&nbsp&nbsp</div>
                    <div class="bar2-wind">{{ weatherData.win }}</div>
                    <div class="bar2-speed">{{ weatherData.win_speed }}</div>
                </div>
            </div>
        </div>
    </div>
    <div class="box2">
        <div class="charts" ref="chart"></div>
    </div>
    <div class="box3">

    </div>
</template>
<script>
import axios from 'axios';
import * as echarts from 'echarts';
export default{
    data(){
        return{
            weatherData:'',
            chart:'',
            items:[],
        }
    },
    created(){
        // this.getWeather()
    },
    mounted(){
        this.getWeather()
        this.drawCharts()
    },
    methods:{
        getWeather(){
           const response = axios.get('http://v1.yiketianqi.com/api?unescape=1&version=v9&appid=84686773&appsecret=JunYchW8')
        //    http://v1.yiketianqi.com/free/day?appid=84686773&appsecret=JunYchW8&unescape=1
           .then(response => {  
                this.weatherData = response.data;
                this.items = response.data.data  
                console.log(this.weatherData);  
                console.log(this.items);  
            })
            .catch(error => {  
                console.error('请求天气数据时出错:', error);  
            }); 
        },
        drawCharts(){
            this.chart = echarts.init(this.$refs.chart);
            const option={
                title:{
                    text:"图表"
                },
                xAxis:{
                    type: 'category',
                    data:["1","2","3","4","5"],
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
                    splitLine:{
                        show:false,
                    },
                    axisLabel: {  
                        show: true,
                        interval:10,  
                        formatter: '{value} ℃'   
                    },
                    axisLine:{
                        lineStyle:{
                            color:'#fff',
                        }
                    }  
                },
                series: [{  
                    name: '销量',  
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
                    data: [18, 16, 26, 17, 19, 20]  
                        }]  
            }
            this.chart.setOption(option);
        }
    }
}
</script>
<style>
.box1{
    margin-left: auto;
    margin-right: auto;
    /* background-color: wheat; */
    height: 150px;
    width: 650px;
}
.box1-bar1{
    display: flex;
    justify-content: space-between;
    height: 25px;
    width: 100%;
}
.Lbar1{
    display: flex;
}
.bar1-city{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 20px;
}
.bar1-tem{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 10px;
}
.bar1-wind{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 10px;
}
.bar1-date{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 10px;
}
.bar1-week{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 10px;
}
.bar1-lunar{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
}
.box1-bar2{
    display: flex;
    /* background-color: aquamarine; */
    height: 100px;
    width: 100%;
}
.bar2-tem{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    padding:5px 5px 0px 5px;
    color: white;
    font-size: 35px;
}
.bar2-otem{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
}
.bar2-air{
    display: flex;  
    flex-direction: column;
    justify-content: flex-end;
    color: white;
    font-size: 10px;
}
.bar2-others{
    display: flex;
    align-items: end;
    color: white;
}
.box2{
    margin-left: auto;
    margin-right: auto;
    background-color: rgba(64, 60, 60, 0.3);
    height: 200px;
    width: 650px;
    border-radius: 3px;
}
.charts{
    margin-left: auto;
    margin-right: auto;
    width: 80%;
    height: 250px;
}
.box3{
    margin-left: auto;
    margin-right: auto;
    height: 100px;
    width: 650px;
    /* background-color: red; */
}
</style>