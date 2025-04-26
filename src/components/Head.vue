<template>
    <div class="bg-lux-green-1">
        <swiper
            :direction="'vertical'"
            :effect="'creative'"
            :pagination="pagination" 
            @slideChange="onSlideChange"
            :creativeEffect="{
              prev: {
                shadow: true,
                translate: [0, 0, -800],
                rotate: [180, 0, 0],
              },
              next: {
                shadow: true,
                translate: [0, 0, -800],
                rotate: [-180, 0, 0],
              },
            }"
            :modules="modules"
            class="mySwiper"
        >
            <swiper-slide v-for="(component, index) in components" :key="index">
                <component :is="component" :key="activeSlide" :triggerAnimation="activeSlide === index" />
            </swiper-slide>
          <!-- <swiper-slide>Slide 2</swiper-slide> -->
        </swiper>
    </div>
  </template>
  <script>
    // components
  import MainHead from './Main/MainHead.vue';

  import Introduction from './Main/Introduction.vue';

    // Import Swiper Vue.js components
    import { Swiper, SwiperSlide } from 'swiper/vue';
  
    // Import Swiper styles
    import 'swiper/css';
  
    import 'swiper/css/pagination';
  
    import './style.css';
  
    // import required modules
    import { Pagination } from 'swiper/modules';

    import { EffectCreative } from 'swiper/modules';
  
    export default {
      components: {
        Swiper,
        SwiperSlide,
        MainHead,
      },
        setup() {
            return {
                activeSlide: 0,
                components: [MainHead ,Introduction],
                pagination: {
                    clickable: true,
                    renderBullet: function (index, className) {
                        return '<span class="' + className + '">' + (index + 1) + '</span>';
                    },
                },
            modules: [Pagination, EffectCreative],
            };
        },
        methods: {
            onSlideChange(swiper) {
                console.log('hi');
                this.activeSlide = swiper.activeIndex;
            }
        }
    };
  </script>
  