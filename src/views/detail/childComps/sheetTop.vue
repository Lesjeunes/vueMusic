<template>
<div class="sheet-top" >
  <img :src="playlist.coverImgUrl" alt="">
  <div class="top-bar">
    <div class="back">
      <svg class="icon" aria-hidden="true" @click="$router.back()">
        <use xlink:href="#icon-back_android"></use>
      </svg>
      <span class="tit">歌单</span>
    </div>
    <div class="right">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-search-copy"></use>
      </svg>
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-more"></use>
      </svg>
    </div>
  </div>
  <div class="center">
    <div class="center-left">
      <img :src="playlist.coverImgUrl" alt="">
      <div class="count">
        <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-play"></use>
          </svg>
        <span>{{ changeCount( playlist.playCount ) }}</span>
      </div>
    </div>
    <div class="center-right">
      <div class="center-name">
        {{ playlist.name }}
      </div>
   <div class="center-per">

      <img :src="playlist.creator.avatarUrl" alt="">-->
      <span>{{ playlist.creator.nickname }}</span>
      <p>{{ playlist.description }}</p>
      </div>
    </div>
  </div>
  <div class="iconlist">
    <div class="icon-item">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-comments"></use>
      </svg>
      <p>{{ playlist.commentCount }}</p>
    </div>
    <div class="icon-item">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-share"></use>
      </svg>
      <p>{{ playlist.shareCount }}</p>
    </div>
    <div class="icon-item">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-download"></use>
      </svg>
      <p>下载</p>
    </div>
    <div class="icon-item">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-check"></use>
      </svg>
      <p>多选</p>
    </div>
  </div>
</div>
</template>

<script>
import {reactive, onMounted, onBeforeMount,defineProps,toRefs} from "vue";
export default {
  name: "sheetTop",
  props:{
    playlist:{
      type:Object
    }
  },

  methods:{
    changeCount(num){
      let res
      if (num > 100000000){
        res = num / 100000000
        res = res.toFixed(2) + '亿'
      }else if (num > 10000){
        res = num / 10000
        res = res.toFixed(2) + '万'
      }
      return res
    }
  }
}
</script>

<style scoped>
.top-bar{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.sheet-top>img{
  display: block;
  width: 100%;
  position: absolute;
  z-index: -1;
  left: 0;
  top: 0;
  filter: blur(20px);
}
.sheet-top{
  padding: 0 ;

}
.tit{
  font-size: 0.34rem;
  color: #fff;
  line-height: 0.5rem;
}
.back,.right{
  display: flex;
  gap: 0.65rem;
}
.center{
  display: flex;
  justify-content: space-between;
}
.center-left{
  flex: 1;
  position: relative;
  border-radius: 0.25rem;
  overflow: hidden;
}
.center-left img{
  display: block;
  width: 100%;
}
.center-left .count{
  position: absolute;
  top: 0.1rem;
  right: 0.1rem;
  font-size: 0.18rem;
  color: #fff;
  display: flex;
  align-items: center;
}
.center-left .count .icon{
  width: 0.35rem;
  height: 0.35rem;
}
.center-right{
  flex: 2;
  padding-left: 0.25rem;
}
.center-name{
  display: -webkit-box;
  font-size: 0.29rem;
  font-weight: 600;
  line-height: 1.4;
  color: #fff;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  height: 0.8rem;
}
.center-per img{
  width: 0.45rem;
  height: 0.45rem;
  border-radius: 50%;
  vertical-align: middle;
}
.center-per span{
  font-size: 0.2rem;
  color: #fff;
  margin-left: 0.2rem;
  vertical-align: middle;
}
.center-per p{
  font-size: 0.18rem;
  color: #fff;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  text-overflow: ellipsis;
  overflow: hidden;
 padding-top: 0.1rem;
}
.center-per{
  margin-top: 0.1rem;

}
.center{
  margin-top: 0.45rem;
}
.iconlist{
  display: flex;
  justify-content: space-around;
  margin-top: 0.45rem;
}
.iconlist p{
  font-size: 0.24rem;
  color: #fff;
  text-align: center;
  margin-top: 0.1rem;

}
</style>