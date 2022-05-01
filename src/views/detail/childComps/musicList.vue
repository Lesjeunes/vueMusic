<template>
<div class="music-list">
  <div class="list-tit">
    <div class="list-play">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-play1"></use>
      </svg>
      <div>
        <div class="tit">播放全部</div>
        <div class="num">(共{{playlist.trackCount}}首)</div>
      </div>
    </div>
    <button class="btn">+&nbsp;收藏&nbsp;({{playlist.subscribedCount}})</button>
  </div>
  <div class="list">
    <div class="list-item" v-for="(item,index) in playlist.tracks" key="index" @click="getMusicId(item)">
      <div class="left">
        <div class="index">{{index + 1}}</div>
        <div class="content">
          <div class="tit">{{item.name}}</div>
          <div class="music-info">
            <span>{{item.ar[0].name}}&nbsp;-&nbsp;</span>
            <span>{{item.al.name}}</span>
          </div>

        </div>
      </div>
      <div class="right">
        <svg class="icon" aria-hidden="true"  v-show="item.mv">
          <use xlink:href="#icon-Play-copy"></use>
        </svg>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-more-copy"></use>
        </svg>
      </div>
    </div>
  </div>
</div>
</template>

<script>

export default {
  name: "musicList",
  data(){
    return{
      musicId:Number
    }
  },
  props:{
    playlist: {
      type:Object
    }
  },
  methods:{
    getMusicId(id){
     this.$store.commit('setPlayList',id)
    }
  }
}
</script>

<style scoped>
.music-list{
  background: #fff;
  border-radius: 0.2rem 0.2rem 0 0;
  margin: 0.3rem -0.25rem;
  padding:  0.25rem;
}
.list-tit{
  display: flex;
  justify-content: space-between;
}
.list-play,.list-play>div {
  display: flex;
  align-items: center;
}
.list-play .tit{
  font-size: 0.28rem;
  color: #000;
  font-weight: 600;

}
.list-play>div {
  display: flex;
  align-items: center;
  gap: 0.1rem;
  margin-left: 0.3rem;
}
.list-play .num{
  font-size: 0.24rem;
  color: #333333;
}
.btn{
  outline: none;
  border: none;
  background: orangered;
  color: #fff;
  font-size: 0.24rem;
  padding: 0.1rem 0.2rem;
  border-radius: 0.25rem;
}

.list-item{
  display: flex;
  justify-content: space-between;
  margin-top: 0.25rem;
}
.list-item .left .index{
  font-size: 0.26rem;
  color: #333;
  width: 0.5rem;
  text-align: center;
}
.list-item .content .tit{
  font-size: 0.26rem;
  color: #111111;
}
.list-item .content .music-info {
  font-size: 0.22rem;
  color: #333333;
  white-space: nowrap;
  width: 5rem;
  overflow: hidden;
  text-overflow: ellipsis;

}
.list-item .left{
  display: flex;
  align-items: center;
  gap: 0.3rem;
  overflow: hidden;

}
.list-item .right{
  display: flex;
  align-items: center;
  gap: 0.2rem;
}
.list-item .right .icon{
  width: 0.35rem;
  height: 0.35rem;
}
</style>