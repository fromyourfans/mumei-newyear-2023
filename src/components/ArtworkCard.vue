<script setup>
defineProps({
  info: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="card">
    <div class="card-box">
      <a :href="info.file" target="_blank">
        <img :src="info.file" alt="">
      </a>
      <div class="card-artist">{{info.artist}}</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  flex-grow:1;
  width: 300px;
  margin: 0px 5px 20px 5px;
  .card-box {
    padding:0px 0px 30px 0px;
    width: 100%;
    height:300px;
    position:relative;
    border: 2px solid #f0f0f0;
    background:#114a4b;
    overflow:hidden;
    img {
      display:inline-block;
      width: 100%;
      position: relative;
      top: 50%;
      transform: translateY(-50%);
    }
    .card-artist {
      height:36px;
      line-height:36px;
      text-align:center;
      color:#131313;
      background:#f0f0f0;
      font-size:18px;
      font-weight:bold;
      position:absolute;
      bottom: 0;
      left: 0;
      right: 0;
    }
  }
}
</style>
