<script setup>
import axios from 'axios';
import MessageCard from '@/components/MessageCard.vue';
</script>

<template>
  <v-container class="content-grid pt-8">
      <!-- MURAL -->
      <v-row no-gutters class="mb-2">
        <v-col>
          <div class="section-header">COMMUNITY MURAL</div>
        </v-col>
      </v-row>
      <v-row no-gutters class="mb-8">
        <v-col sm="10" offset-sm="1">
          <div class="section-body mural-container">
            <img src="https://mumei500k.fromyour.fans/img/mural1.b34eb720.png" class="mural-img">
            <!-- <img src="@/assets/banner.png" class="mural-img"> -->
          </div>
        </v-col>
      </v-row>

      <!-- MESSAGES -->
      <v-row no-gutters class="mt-8 mb-4">
        <v-col>
          <div class="section-header">MESSAGES</div>
        </v-col>
      </v-row>
      <v-row no-gutters>
        <v-col>
          <div class="section-body cards-container">
            <MessageCard v-for="(item, ix) in cards" :key="`card-${ix}`" :info="item" />
          </div>
        </v-col>
      </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      source: 'https://vtubertools.sfo3.digitaloceanspaces.com/tribute/mumei500k.json',
      cards: [],
    }
  },
  mounted() {
    (async () => {
      const fetchSource = await axios.get(this.source).catch(() => null);
      const data = fetchSource && fetchSource.data ? fetchSource.data : { messages: {} };
      this.cards = Object.values(data.messages).sort((a, b) => a.time - b.time);
    })();
  },
}
</script>

<style lang="scss" scoped>
.content-grid {
  .section-header {
    width:94%;
    margin:0px auto 20px;
    background:#59b4b6;
    color:#000000;
    border-radius:20px;
    font-size:24px;
    height:40px;
    line-height:40px;
    text-align:center;
    font-weight:bold;
  }
  .section-body {
    width:90%;
    margin:0px auto 40px;
    color:#000000;
    &.mural-container {
      .mural-img {
        width:100%;
      }
    }
    &.cards-container {
      display: flex;
      flex-wrap: wrap;
    }
  }
}
</style>
