<template>
  <div>
    <el-collapse v-model="activeNames">
      <el-collapse-item title="随机英雄" name="1">
        <PickHero v-if="heros.length>0" :inHeros="heros"/>
      </el-collapse-item>
      <el-collapse-item title="英雄列表" name="2">
        <HeroList v-if="heros.length>0" :inHeros="heros"/>
      </el-collapse-item>
    </el-collapse>

  </div>
</template>
<style>

</style>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios'
import HeroList from '@/components/HeroPicker/HeroList.vue'
import PickHero from '@/components/HeroPicker/PickHero.vue';

export default defineComponent({
  name:"HeroPicker",
  data(){
    return{
      activeNames:"",
      heros: [] as any[]
    }
  },
  components:{
    HeroList,
    PickHero
}
  ,
  mounted(){
    if(this.$data.heros.length == 0){
      axios.get("https://game.gtimg.cn/images/lol/act/img/js/heroList/hero_list.js").then((Response)=>{
        this.$data.heros = Response.data.hero
      })
    }
    
  },
  methods: {
    //
  }

})

</script>
