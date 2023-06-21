<template>
  <div>
    <h1>Swiper - Vue</h1>
    <!-- <client-only> -->
    <!-- :slides-per-view="4" -->
    <!-- space-between="24" -->
    <!-- loop
      autoplay
      @swiper="onSwiper"
      @slideChange="onSlideChange" -->
    <swiper-container ref="swiper" :init="false" class="carousel-style">
      <swiper-slide
        v-for="(el, i) in [0, 1, 2, 3, 4, 5, 6, 7]"
        :key="i"
        loop
        class="video-card"
        @mouseenter="playVideo(i)"
        @mouseleave="pauseVideo(i)"
      >
        <h1>{{ i }}</h1>
        <!-- <div class="video-container" :class="{ active: currentIndex == i }"> -->
        <div class="video-container">
          <video
            :id="`carrouselVideo${i}`"
            loop
            muted
            playsinline
            :controls="false"
          >
            <source src="https://cdn.sandbox.game/home/Hero-Video-low.mp4" />
          </video>
          <!-- <nuxt-img
              class="partner-logo"
              src="/img/00_General/testpartnerlogo.png"
              alt="Partner Logo"
              height="64"
            /> -->
        </div>
      </swiper-slide>
    </swiper-container>
    <!-- </client-only> -->
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
// import {useSwiper} from 'swiper/vue'
// Import Swiper Vue.js components

// Import Swiper styles
// import "swiper/css";

export default {
  name: "IndexPage",
  setup() {
    // const swiper = ref(null);
    // const swiperSlide = ref(null);
    // //REF:: https://swiperjs.com/vue#useswiper
    // const swiper = useSwiper();
    // //REF:: https://swiperjs.com/vue#useswiperslide
    // const swiperSlide = useSwiperSlide();
    const onSwiper = (swiper) => {
      console.log("1)) onSwiper:: ", { swiper });
    };
    const onSlideChange = (ev) => {
      // console.log("onSlideChange:: ", { ev });
      // // console.log("activeIndex:: ", swiper.value.activeIndex);
      // console.log("swiperSlide:: ", { swiperSlide: swiperSlide.value });
    };

    function playVideo(index) {
      const video = document.getElementById(`carrouselVideo${index}`);
      video?.play();
    }
    function pauseVideo(index) {
      const video = document.getElementById(`carrouselVideo${index}`);
      video?.pause();
      video.currentTime = 0;
    }
    return {
      // swiper,
      onSwiper,
      onSlideChange,
      playVideo,
      pauseVideo,
    };
  },
  created() {
    if (!process.server) {
      setTimeout(() => {
        console.log("swiper: ", this.$refs.swiper);
        const swiperEl = this.$refs.swiper;
        // spaceBetween: 24,
        Object.assign(swiperEl, {
          centeredSlides: false,
          breakpoints: {
            "@0.00": {
              slidesPerView: 1,
              spaceBetween: 10,
            },
            "@0.50": {
              slidesPerView: 2,
              spaceBetween: 20,
            },
            "@0.75": {
              loop: true,
              centeredSlides: true,
              slidesPerView: 1.3,
              spaceBetween: 40,
            },
            "@1.00": {
              slidesPerView: 4,
              spaceBetween: 50,
            },
            //   1200: {
            //     centeredSlides: false
            //   },
            //   1024: {
            //     slidesPerView: 4,
            //   },
            //   768: {
            //     slidesPerView: 1.2,
            //     centeredSlides: true,
            //   },
            //   1: {
            //     slidesPerView: 1,
            //   },
          },
        });

        swiperEl.initialize();
      }, 100);
    }
  },
};
</script>


<style lang="scss" scoped>
swiper-slide {
  width: 60%;
}

swiper-slide:nth-child(2n) {
  width: 40%;
}

swiper-slide:nth-child(3n) {
  width: 20%;
}
.container {
  position: relative;
}
.carousel-style {
  max-width: 1440px;
  :deep(.ssr-carousel-slide) {
    width: 302px;
  }
  .video-card {
    height: 220px;
    background: red;
    // @media ((min-width: 768px) and  (max-width: 1024px)) {
    //   width: 305px !important;
    //   background: blue;
    // }
    .video-container {
      width: 302px;
      height: 160px;
      overflow: hidden;
      position: relative;
      transition: height 0.5s;
      .partner-logo {
        position: absolute;
        left: 50%;
        top: 50%;
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
        transition: transform 0.5s;
      }
      &:hover {
        height: 220px;
        .partner-logo {
          transform: translate(-50%, 80%) scale(0.75);
        }
      }
    }
    video {
      width: 302px;
      height: 220px;
      object-fit: cover;
    }
  }
}

.full-screen-video {
  height: calc(100dvh - var(--navbar-height-redesign));
  width: 100%;
  object-fit: cover;
  position: sticky;
  top: 0;
  z-index: 0;
}
.grid {
  position: sticky;
  top: 0;
  display: grid;
  grid: [a] 1fr / [b] 1fr;
}
.sticky-background {
  grid-area: a / b;
  position: sticky;
  top: 0;
  z-index: 2;
  height: calc(100dvh - var(--navbar-height-redesign));
  background: radial-gradient(
      200% 100% at 100% 0%,
      #0d1015 31.96%,
      rgba(1, 10, 48, 0) 64.77%
    ),
    radial-gradient(
      200% 100% at 0% 100%,
      #0d1015 29.86%,
      rgba(1, 10, 48, 0) 67.84%
    ),
    #020b31;
}
.content {
  grid-area: a / b;
  z-index: 4;
  position: sticky;
  height: calc(100dvh - var(--navbar-height-redesign));
}
</style>
