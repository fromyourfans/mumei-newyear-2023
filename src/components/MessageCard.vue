<script setup>
defineProps({
  info: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="card" >
    <div class="card-img" :style="{ transform: `rotate(${Math.ceil(Math.random() * 10) - 5}deg)` }"></div>
    <div class="card-name">{{info.name}}</div>
    <div class="card-text">{{info.message}}</div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  flex-grow:1;
  padding:80px 30px;
  width: 360px;
  height: 320px;
  margin: 0px 5px 20px 5px;
  position:relative;
  .card-img {
    width: 100%;
    height: 320px;
    background-image: url('../assets/card.png');
    background-repeat: no-repeat;
    background-position: top center;
    background-size: 360px 320px;
    position:absolute;
    z-index:1;
    top:0;
    left:0;
  }
  .card-name {
    color:#000000;
    font-weight:bold;
    text-align:center;
    font-size:18px;
    margin-bottom:20px;
    position:relative;
    z-index:3;
  }
  .card-text {
    color: #262626;
    width:300px;
    margin:0px auto;
    font-size:16px;
    line-height:20px;
    position:relative;
    z-index:2;
  }
}
</style>
