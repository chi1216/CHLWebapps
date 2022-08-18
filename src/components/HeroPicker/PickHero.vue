<template>
  <div style="text-align:left">
    <div v-if="redHeros.length == 0">
    <el-button type="primary" @click="pickHero(5)">随机5个</el-button>
    <el-button type="primary" @click="pickHero(10)">随机10个</el-button>
    <el-button type="primary" @click="pickHero(20)">随机20个</el-button>
    </div>
    <div v-else>
      <el-button type="danger" @click="redHeros=[];blueHeros=[]">清空</el-button>
    </div>
    <h1>红队英雄</h1>
    <HeroList v-if="redHeros.length > 0" :inHeros="redHeros"></HeroList>
    <el-divider></el-divider>
    <h1>蓝队英雄</h1>
    <HeroList v-if="redHeros.length > 0" :inHeros="blueHeros"></HeroList>
  </div>
</template>
<style>

</style>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios'
import HeroList from './HeroList.vue';

export default defineComponent({
    name: "PickHero",
    data() {
        return {
            redHeros: [] as any[],
            blueHeros: [] as any[]
        };
    },
    props: {
        inHeros: Array
    },
    mounted() {
        //
    },
    methods: {
      pickHero(count:number){
        this.redHeros = [];
        this.blueHeros = [];

        let red = [];
        let maxLength = this.inHeros?.length as number - 1;
        let heroList = this.inHeros as any[];

        for(let i = 0; i < count; i++){
          let newNumber = Math.round(Math.random()*maxLength);
          red.push(heroList[newNumber]);
          let temp = heroList[newNumber]
          heroList[newNumber] = heroList[maxLength];
          heroList[maxLength] = temp;

          maxLength--;
        }

        let blue = [];
        //maxLength = this.inHeros?.length as number - 1;

        for(let i = 0; i < count; i++){
          let newNumber = Math.round(Math.random()*maxLength);
          blue.push(heroList[newNumber]);
          let temp = heroList[newNumber]
          heroList[newNumber] = heroList[maxLength];
          heroList[maxLength] = temp;

          maxLength--;
        }
        this.redHeros = red;
        this.blueHeros = blue;
      }
    },
    components: { HeroList }
})

</script>
