<template>
  <div>
    <div class="main-header">
      <h5>{{ $t("main1") }}</h5>
      <h1>{{ $t("main2") }}</h1>
      <h5>{{ $t("main3") }}</h5>
      <div class="deliner"></div>
    </div>
  </div>
  <swiper
    class="bestswip"
    :modules="modules"
    :slides-per-view="1"
    :space-between="50"
    navigation
    :pagination="{ clickable: true }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <swiper-slide
      ><img src="../assets/slider-img/1.jpg" alt="bad gaterway" class="swip"
    /></swiper-slide>
    <swiper-slide
      ><img src="../assets/slider-img/2.jpg" alt="bad gaterway" class="swip"
    /></swiper-slide>
    <swiper-slide
      ><img src="../assets/slider-img/4.jpg" alt="bad gaterway" class="swip"
    /></swiper-slide>
  </swiper>
  <div class="products">
    <div class="products-header">
      <h1>{{ $t("main4") }}</h1>
      <h5>{{ $t("main5") }}</h5>
      <div class="deliner"></div>
      <h5>{{ $t("main6") }}</h5>
    </div>
    <h1>{{ $t("main7") }}</h1>
  </div>
  <div class="products-name">
    <RouterLink to="/" class="products-class">
      <div class="sw products-class actived">
        <h3>{{ $t("selector1") }}</h3>
      </div>
    </RouterLink>
    <RouterLink to="/benches" class="products-class">
      <div class="products-class gd">
        <h3>{{ $t("selector2") }}</h3>
      </div>
    </RouterLink>
    <RouterLink to="/sets" class="products-class">
      <div class="products-class pg">
        <h3>{{ $t("selector3") }}</h3>
      </div>
    </RouterLink>
  </div>
  <RouterView> </RouterView>
</template>

<script>
import { Navigation, Pagination, Scrollbar, A11y } from "swiper/modules";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "swiper/css/scrollbar";
export default {
  name: "main-page",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const onSwiper = (swiper) => {
      console.log(swiper);
    };
    const onSlideChange = () => {
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Navigation, Pagination, Scrollbar, A11y],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.swip {
  border-radius: 2.2vmin;
  height: 70vmin;
  width: 80%;
}
.bestswip {
  z-index: 19999998;
  margin-top: 3vmin;
  width: 45%;
}
.swiper-button-next {
  z-index: 99999999;
}
.swiper-button-prev {
  z-index: 99999999;
}
.carousel__item {
  min-height: 210px;
  width: 33%;
  background-color: red;
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.carousel__item img {
  border-radius: 2vmin;
  height: 49vmin;
  width: 100%;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
}
ol {
  padding: 0;
}
  @media (max-width: 920px) {
    .swip {
      width: 100%;
      height: unset;
    }
    .bestswip {
      width: 85%;
      height: auto;
    }
   }
</style>
