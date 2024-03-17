<template>
    <div class="card-container">
        <div class="card-header">
            <div class="card-header-left">
                <div class="card-city">{{ weatherData?.city }}</div>
                <div class="card-wea">今天：{{ currentweatherData?.wea }} {{nowweatherData?.tem2}}°~{{nowweatherData?.tem1}}°C</div>
                <div class="card-win">{{nowweatherData?.win[0]}}{{nowweatherData?.win_speed}}</div>
            </div>
            <div class="card-header-right">
                <div class="card-date">{{nowweatherData?.date}}</div>
                <div class="card-week">{{nowweatherData?.week }}</div>
                <div class="card-lunar"></div>
            </div>
        </div>
        <div class="card-body">
            <div class="card-body-left">
                <div class="card-tem">{{currentweatherData?.tem }}°</div>
            </div>
            <div class="card-body-right">
                <div class="card-body-rightT">
                    <div class="card-air">{{nowweatherData?.air }}</div>
                    <div class="card-airq">{{nowweatherData?.air_level }}</div>
                </div>
                <div class="card-body-rightB">
                    <div class="weather-img"><img class="cloudimg" src="../../assets/cloud06.svg"></div>
                    <div class="card-cld">{{currentweatherData?.wea}}</div>
                    <div class="card-windir">{{currentweatherData?.win}}</div>
                    <div class="card-winspeed">{{currentweatherData?.win_speed }}</div>
                </div>
            </div>
        </div>
        <div class="card-footer">
            <div class="card-footer-content">湿度{{nowweatherData?.humidity}}</div>
            <div class="card-footer-content">{{nowweatherData?.index[0]?.title}}{{nowweatherData?.index[0]?.level}}</div>
            <div class="card-footer-content">日出{{ nowweatherData?.sunrise }}</div>
            <div class="card-footer-content">日落{{ nowweatherData?.sunset }}</div>
        </div>
    </div>
</template>
<script>
export default{
    
    mounted(){
            console.log(this.weatherData)
            console.log(this.nowweatherData)
    },
    props:['weather-data','nowweatherData','currentweatherData']
    
}
</script>
<style>
.card-container{
    width: 100%;
    height: 188px;
    padding: 30px 0;
}
.card-header{
    display: flex;
    justify-content: space-between;
    height: 26px;
}
.card-header-left{
    display: flex;
    color: white;
    align-items:end;
    font-size: 14px;
    gap: 15px;
}
.card-city{
    font-size: 20px;
}
.card-header-right{
    display: flex;
    color: white;
    align-items: end;
    font-size: 14px;
    gap: 15px;
}
.card-body{
    display: flex;
    align-items: center;
    height: 79px;
    margin-top: 45px;
    color: white;
    overflow: hidden;
}
.card-tem{
    font-size: 79px;
}
.card-body-right{
    display: flex;
    flex-direction: column;
    margin-top: 20px;
    margin-left: 30px;
    height: 53px;
    width: 200px;
    overflow: hidden;
}
.card-body-rightT{
    background: rgb(130, 201, 30);
    border-radius: 9.5px;
    height: 19px;
    width: 30px;
    display: flex;
    padding: 0 6px;
    font-size: 12px;
}
.card-air{
    margin-right: 3px;
}
.card-body-rightB{
    display: flex;
    gap: 10px;
    font-size: 14px;
    margin-top: 10px;
    height: 22px;
    width: 200px;
    overflow: hidden;
}
.weather-img{
    width: 20px;
    height: 20px;
    transform: translateX(30%);
}
.cloudimg{
    width: 20px;
    height: 20px;
    transform: scale(1.5);
}
.card-footer{
    display: flex;
    margin-top: 30px;
    color: white;
    font-size: 14px;
}
.card-footer-content{
    margin-right: 20px;
}

</style>