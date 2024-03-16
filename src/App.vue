<template>
  <div class="Gamezone">
    <Weather></Weather>
  </div>
</template>

<script>
import Weather from './components/Weather.vue';
import * as echarts from 'echarts';
export default{
components:{
  Weather
}
}
</script>

<style>
body{
  padding: 0;
  margin: 0;
  background: linear-gradient(to bottom, rgb(93, 115, 215), rgb(254, 178, 190),rgb(93, 115, 215));
  background-size: cover;
  background-repeat: no-repeat;
  min-height: 600px;
  
}
.Gamezone{
position: absolute;
left: 50%;
top: 50%;
transform: translate(-50%,-50%);
}
.title{
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-weight: 900;
  font-size: 32px;
}
</style>