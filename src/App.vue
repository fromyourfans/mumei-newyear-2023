<script setup>
import { RouterView } from 'vue-router'
</script>

<template>
  <main>
    <div>
      <!-- HEADER -->
      <div class="header">
        <img src="@/assets/hny.png">
      </div>

      <!-- CONTENT -->
      <div class="content">
        <RouterView />
      </div>
    </div>
  </main>
</template>

<style scoped>
.header {
  width:100%;
  height:240px;
  background-image:url("@/assets/banner.png");
  background-position: -40% center;
  background-size:auto 115%;
  background-repeat: repeat-x;
  background-color:#288485;
  display: flex;
}
.header img {
  margin:auto;
  max-width:96vw;
  max-height:220px;
}
.content {
  min-height:calc(100vh - 360px);
  background:linear-gradient(to bottom, #288485 0%, #124a4b 400px, #288485 100%);
  padding:30px 10px 10px 10px;
}
</style>
