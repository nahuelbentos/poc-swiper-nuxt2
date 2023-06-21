<template>
  <VueSlickCarousel :arrows="true" :dots="true">
    <div>
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
    </div>
    <div>
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
    </div>
    <div>
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
    </div>
    <div>
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
    </div>
  </VueSlickCarousel>
</template>

<script>
// register();

import VueSlickCarousel from "vue-slick-carousel";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  components: { VueSlickCarousel },
  setup() {
    const spaceBetween = 10;
    const onProgress = (e) => {
      const [swiper, progress] = e.detail;
      console.log(progress);
    };

    const onSlideChange = (e) => {
      console.log("slide changed");
    };

    return {
      spaceBetween,
      onProgress,
      onSlideChange,
    };
  },
};
</script>
