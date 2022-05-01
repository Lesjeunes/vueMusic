<template>
<div class="top-bar">
  <div class="menu">
    <svg class="icon" aria-hidden="true">
      <use xlink:href="#icon-menu"></use>
    </svg>
  </div>
  <tab-control class="tab-control"
               :titles="['我的','发现','云村','视频',]"
  ></tab-control>
  <div class="search">
    <svg class="icon" aria-hidden="true">
      <use xlink:href="#icon-search"></use>
    </svg>
  </div>
</div>
</template>

<script>
import tabControl from "@/components/content/tabControl/tabControl";
export default {
  name: "topBar",
components:{
    tabControl
},
  data:function (){
    return {

    }
  }
}
</script>

<style scoped>
.top-bar{
  display: flex;
  justify-content: space-between;
  font-size: 1rem;
  line-height: 1.5rem;
  padding: 0.35rem;
}
</style>