<template>
    <div class="card-container">
        <div class="card-header">
            <div class="card-header-left">
                <div class="card-city">杭州</div>
                <div class="card-wea">今天：小雨 8°~17°C</div>
                <div class="card-win">无持续风向&lt;3级</div>
            </div>
            <div class="card-header-right">
                <div class="card-date">03月17日</div>
                <div class="card-week">周日</div>
                <div class="card-lunar">农历二月初八</div>
            </div>
        </div>
        <div class="card-body">
            <div class="card-body-left">
                <div class="card-tem">16°</div>
            </div>
            <div class="card-body-right">
                <div class="card-body-rightT">
                    <div class="card-air">62</div>
                    <div class="card-airq">良</div>
                </div>
                <div class="card-body-rightB">
                    <div class="weather-img"><img class="cloudimg" src="../../assets/cloud06.svg"></div>
                    <div class="card-cld">阴</div>
                    <div class="card-windir">东北风</div>
                    <div class="card-winspeed">4级</div>
                </div>
            </div>
        </div>
        <div class="card-footer">
            <div class="card-footer-content">湿度67.0%</div>
            <div class="card-footer-content">紫外线最弱</div>
            <div class="card-footer-content">日出06:07</div>
            <div class="card-footer-content">日落18:09</div>
        </div>
    </div>
</template>
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
.card-wea{
  
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
    width: 140px;
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
    width: 140px;
    overflow: hidden;
}
.weather-img{
    width: 30px;
    height: 30px;
}
.cloudimg{
    width: 30px;
    height: 30px;
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