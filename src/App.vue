<template>
  <div class="container">
    <Header></Header>
    <div class="body">
        <Card></Card>
    </div>
  </div>
</template>

<script>
import Weather from './components/Weather.vue';
import Header from './components/Header/index.vue';
import Card from './components/Card/index.vue';
import Chart from './components/Chart/index.vue';
export default{
components:{
  Weather,
  Header,
  Card,
  Chart
}
}
</script>

<style>
html,p,body{
    margin: 0;
    padding: 0;
}
.container{
    width: 100%;
    min-height: 600px;
    background: linear-gradient(rgb(72, 86, 99), rgb(161, 184, 202));
}
.body{
  width: 895px;
  margin: 0 auto;
  /* background-color: black; */
  /* background: linear-gradient(rgb(72, 86, 99), rgb(161, 184, 202)); */

}
/* body{
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
width: 650px;
} */

</style>