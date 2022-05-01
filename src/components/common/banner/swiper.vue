<template>
  <swiper
      :modules="modules"
      :slides-per-view="1"
      :space-between="10"
      :loop="true"
      :pagination="{ clickable: true }"
      :autoplay="{delay: 1500}"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
  >
    <swiper-slide v-for="(item,i) in banner" key="i"><img :src="item.pic " alt=""></swiper-slide>

  </swiper>
</template>
<script>
// import Swiper core and required modules
import {  Pagination ,Autoplay} from 'swiper';

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';

import 'swiper/css/pagination';


// Import Swiper styles
export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  props:{
    banner:{
      type: Array,
      default() {
        return [];
      }
    }
  },
  setup() {
    const onSwiper = (swiper) => {
      //console.log(swiper);
    };
    const onSlideChange = () => {
      //console.log('slide change');
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Pagination,Autoplay],
    };
  },
};
</script>
<style scoped>
.swiper img{
  display: block;
  width: 100%;
  border-radius: 0.5rem;
}

::v-deep .swiper-pagination-bullets {
  bottom: 0.2rem !important;
}
::v-deep .swiper-pagination-bullet-active{
  background: orangered;
}
</style>