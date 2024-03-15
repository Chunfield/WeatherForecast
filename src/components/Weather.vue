<template>
    <div class="box1">
        <div class="box1-bar1">
            <div class="Lbar1">
            <span class="bar1-city">{{ weatherData.city}}&nbsp&nbsp</span>
            <span class="bar1-tem">今天：{{weatherData.wea}}&nbsp&nbsp{{ weatherData.tem_night }}~{{weatherData.tem_day}}℃&nbsp&nbsp</span>
            <div class="bar1-wind">{{ weatherData.win }}{{ weatherData.win_speed }}</div>
            <div class="bar1-hum"></div>
            </div>
         <div class="Lbar1">
            <div class="bar1-date">{{ weatherData.date }}&nbsp&nbsp</div>
            <div class="bar1-week">{{ weatherData.week }}</div>
            <div class="bar1-lunar"></div>
            </div>
        </div>
        <div class="box2-bar2">
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

    </div>
    <div class="box3">

    </div>
</template>
<script>
import axios from 'axios';
export default{
    data(){
        return{
            weatherData:'',
        }
    },
    created(){
        // this.getWeather()
    },
    mounted(){
        this.getWeather()
        
    },
    methods:{
        getWeather(){
            
           const response = axios.get('http://v1.yiketianqi.com/free/day?appid=84686773&appsecret=JunYchW8&unescape=1')
           .then(response => {  
                this.weatherData = response.data;  
                console.log(this.weatherData);  
                console.log(this.weatherData.tem_day);  
            })
            .catch(error => {  
                console.error('请求天气数据时出错:', error);  
            }); 
        }
    }
}
</script>
<style>
.box1{
    margin-left: auto;
    margin-right: auto;
    /* background-color: wheat; */
    height: 160px;
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
.box2-bar2{
    display: flex;
    /* background-color: aquamarine; */
    height: 100px;
    width: 100%;
}
.box2{
    margin-left: auto;
    margin-right: auto;
    background-color: azure;
    height: 150px;
    width: 650px;
    margin-top: 20px;
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
.box3{
    margin-left: auto;
    margin-right: auto;
    height: 100px;
    width: 650px;
    background-color: red;
}
</style>