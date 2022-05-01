<template>
<div class="song-detail">
  <sheet-top :playlist="state.playlist"></sheet-top>
  <music-list :playlist="state.playlist"></music-list>
</div>
</template>

<script>
import sheetTop from "@/views/detail/childComps/sheetTop";
import musicList from "@/views/detail/childComps/musicList";
import {reactive, onMounted, onBeforeMount} from "vue";
import {useRoute} from 'vue-router'

import {getPlayList} from "@/network/icon";

export default {
  name: "songDetail",
  setup(){
    let route = useRoute()
    let state = reactive({
      playlist:{
        creator:{},
        tracks:{}
      }})
    onMounted(()=>{
      let id  = route.query.id
      getPlayList(id).then( res => {
        state.playlist = res.playlist
        //console.log(state.playlist);
      })
    })
    return{
      state
    }
  },
  components:{
    sheetTop,
    musicList
  }



}
</script>

<style scoped>

</style>