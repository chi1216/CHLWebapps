<template>
  <div>
    <ul class="hero-list">
      <li class="list-item" @click="play(item.selectAudio)" v-for="(item, index) in heros" :key="index">
        <div class="hero-item">
          <div class="hero-pic">
            <img :src="getSrc(item)"/>
          </div>
          <p class="hero-name">
            {{item.name}}
          </p>
        </div>
      </li>
    </ul>
    

  </div>
</template>
<style>
.hero-list .list-item .hero-item .hero-pic .hero-position {
    position: absolute;
    top: 0.1rem;
}
.icon-pos-sup {
    background-position: 0.02rem 0.02rem;
    width: 0.26rem;
    height: 0.22rem;
}
.icon-pos-top {
    background-position: -0.25rem 0.02rem;
    width: 0.23rem;
    height: 0.23rem;
}
.icon-pos-jungle {
    background-position: -0.49rem 0.02rem;
    width: 0.22rem;
    height: 0.24rem;
}
.icon-pos-mid {
    background-position: -0.25rem -0.22rem;
    width: 0.22rem;
    height: 0.22rem;
}
.icon-pos-bot {
    background-position: 0.02rem -0.21rem;
    width: 0.23rem;
    height: 0.23rem;
}
.icon-arrow-down, .icon-gold, .icon-pos-bot, .icon-pos-jungle, .icon-pos-mid, .icon-pos-sup, .icon-pos-top, .icon-search, .spr_info_overview {
    background-image: url(//game.gtimg.cn/images/lol/lolstrategy/spr_info_overview.png?2022_1_19_17_20_44);
    background-size: 0.69rem 0.59rem;
    background-repeat: no-repeat;
}
.hero-list .list-item .hero-item .hero-name {
    line-height: 1.52rem;
    color: #fff5e0;
    font-size: .14rem;
    text-align: center;
}
.hero-list .list-item .hero-item .hero-pic img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
}
.hero-list .list-item .hero-item .hero-pic {
    height: 11.25rem;
    position: relative;
    overflow: hidden;
}
li {
    display: list-item;
    text-align: -webkit-match-parent;
}
.hero-list {
    margin-top: 0.4rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: start;
}

.hero-list .list-item {
    width: 8.17rem;
    height: 12.77rem;
    margin-right: 0.2rem;
    margin-bottom: 0.2rem;
    position: relative;
    cursor: pointer;
}

.hero-list .list-item .hero-item {
    width: 100%;
    height: 100%;
    background-color: #111419;
    box-sizing: border-box;
    border: 1px solid #313e4c;
    transition: all linear .2s;
    transform-origin: bottom center;
    -webkit-transform-origin: bottom center;
    -moz-transform-origin: bottom center;
    -o-transform-origin: bottom center;
}

ol, td, th, ul {
    padding: 0;
    list-style: none;
}
article, body, dd, dl, footer, form, h1, h2, h3, h4, h5, h6, header, ol, p, section, ul {
    margin: 0;
    margin-top: 0px;
    margin-right: 0px;
    margin-bottom: 0px;
    margin-left: 0px;
}

ul {
    display: block;
    list-style-type: none;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    padding-inline-start: 40px;
}
</style>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name:"HeroList",
  data(){
    return{
      heros:[] as any[]
    }
  },
  props:{
      inHeros: Array
  },
  mounted(){
    this.$data.heros = this.$props.inHeros as any[];
    
  },
  methods: {
    getSrc(hero: any){
      let src = "https://game.gtimg.cn/images/lol/act/img/skinloading/" + (Number(hero.heroId)*1000) + ".jpg"
      return(src)
    },
    play(src: string){
        const player = new Audio(src);
        player.play();
    }
  }

})

</script>
