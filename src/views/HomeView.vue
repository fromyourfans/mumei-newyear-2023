<script setup>
import axios from 'axios';
import MessageCard from '@/components/MessageCard.vue';
import ArtworkCard from '@/components/ArtworkCard.vue';
import muralImg from '@/assets/20221226.png';
import art01 from '@/assets/fanart/01-JesusAlberto.png';
import art02 from '@/assets/fanart/02-MumeisCloak.png';
import art03 from '@/assets/fanart/03-MABIN.png';
import art04 from '@/assets/fanart/04-SyntaxeErrour.png';
import art05 from '@/assets/fanart/05-Day.png';
import art06 from '@/assets/fanart/06-AABA.png';
import art07 from '@/assets/fanart/07-Elious.png';
import art08 from '@/assets/fanart/08-scount.png';
import art09 from '@/assets/fanart/09-MeguminsStaff.png';
import art10 from '@/assets/fanart/10-MoguMogu.png';
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
            <img :src="muralImg" class="mural-img">
          </div>
        </v-col>
      </v-row>

      <!-- GALLERY -->
      <v-row no-gutters class="mt-8 mb-4">
        <v-col>
          <div class="section-header">GALLERY</div>
        </v-col>
      </v-row>
      <v-row no-gutters>
        <v-col>
          <div class="section-body arts-container">
            <ArtworkCard v-for="(info, ix) in arts" :key="`art-${ix}`" :info="info" />
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
      source: 'https://vtubertools.sfo3.digitaloceanspaces.com/tribute/mumei2023.json',
      cards: [],
      arts: [
        { file: art01, artist: 'Jesus Alberto' },
        { file: art02, artist: 'Mumei’s Cloak ' },
        { file: art03, artist: 'MABIN' },
        { file: art04, artist: 'Syntaxe Errour' },
        { file: art05, artist: 'Đay' },
        { file: art06, artist: 'AABABABBBABBAABBA' },
        { file: art07, artist: 'Elious' },
        { file: art08, artist: 'scount' },
        { file: art09, artist: 'Megumin\'s Staff' },
        { file: art10, artist: 'Mogu Mogu' },
      ],
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
    &.arts-container {
      display: flex;
      flex-wrap: wrap;
    }
  }
}
</style>
