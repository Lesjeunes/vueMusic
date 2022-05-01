<template>
<!--默认为空，点击歌曲后获得歌曲的id传入vuex中，在显示出来-->
  <div class="play-control">
    <div class="left">
      <img :src="$store.state.playlist[0].al.picUrl" alt="">
      <div>
        <div class="tit">{{$store.state.playlist[0].name}}</div>
        <div class="tips">点击切换上下曲</div>
      </div>
    </div>
    <div class="right">
     <svg v-if="!isPlay" class="icon" aria-hidden="true" @click="play" >
         <use xlink:href="#icon-pause"></use>
       </svg>
       <svg v-else class="icon" aria-hidden="true" @click="play" >
         <use xlink:href="#icon-play2"></use>
       </svg>

      <svg class="icon" aria-hidden="true" >
        <use xlink:href="#icon-menuon"></use>
      </svg>
  </div>
<audio ref="audio" :src="getMusicUrl($store.state.playlist[0].id)" ></audio>
  </div>
</template>

<script>
import {getMusic} from "@/network/icon";
import {mapState} from 'vuex'
export default {
  name: "playController",
  data(){
    return{
      isPlay:true
    }
  },
  methods:{
    getMusicUrl(id){
      let url =  'https://music.163.com/song/media/outer/url?id=' + id + '.mp3'
      return url
    },
    play(){
      if (this.$refs.audio.paused){
        this.$refs.audio.play()
        this.isPlay = this.$refs.audio.paused
      }else {
        this.$refs.audio.pause()
        this.isPlay = this.$refs.audio.paused
      }

    }
}
}
</script>

<style scoped>
.play-control{
  display: flex;
  justify-content: space-between;
}
.play-control .left{
  display: flex;
  align-items: center;
  gap: 0.2rem;
}
.play-control .left img{
  width: 0.6rem;
  height: 0.6rem;
  border-radius: 50%;
}
.play-control .left .tit{
  font-size: 0.26rem;
  color: #111111;
  font-weight: 600;
}
.play-control .left .tips{
  font-size: 0.2rem;
  color: #333333;
}
.play-control{
  position: fixed;
  left: 0;
  bottom: 0;
  right: 0;
  background: #fff;
  padding: 0.25rem 0.2rem;
}
.play-control .right{
  display: flex;
  align-items: center;
  gap: 0.2rem;
}
</style>