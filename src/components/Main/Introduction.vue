<template>
  <div class="w-full h-full bg-[url(/src/assets/images/head_1.jpg)] bg-no-repeat bg-cover relative">
    <div class="absolute top-0 left-0 w-full h-full opacity-90 bg-lux-green-1"></div>
        <div class="absolute top-0 left-0 w-full h-full md:p-5">
            <div class="p-5 md:border md:border-lux-green-2 rounded-xl w-full h-full flex items-center justify-center">
              <div class="w-full p-5 grid md:md:grid-cols-3 grid-cols-1 md:gap-5">
                <div class="col-span-1">
                  <div class="w-full rounded-xl md:h-[80vh] h-[80vh] text-right pr-5">
                    <div class="pb-2 mb-2 border-b border-lux-green-2">
                      <h3 class="md:text-2xl text-xl yekan-bold">یوسف جعفری</h3>
                      <span class="text-xs text-lux-green-3 yekan-bold">Fullstack web developer</span>
                    </div>
                    <div>
                      <q class="md:text-md text-sm yekan-bold leading-10 text-lux-green-4">{{ txt[Math.floor(Math.random() * (10 - 1) + 1)] }}</q>
                      <p class="md:text-md text-sm leading-10 text-lux-green-4">سلام! من یوسف هستم یک برنامه نویس تمام پشته (Fullstack) وب با +5 سال تجربه در زمنیه توسعه اپلیکیشن های تحت وب و مسلط به فناوریهای مدرن وب.</p>
                    </div>
                    <div class="mt-2">
                      <h3 class="text-md yekan-bold leading-10 text-lux-green-4">مهارت ها</h3>
                      <div class="mt-2">
                        <Skills
                          :active-index="activeIndex" 
                          @slide-change="onSlideChangeB"
                        />
                      </div>
                    </div>
                  </div>
                </div>
                <div class="md:col-span-2 col-span-1 md:block hidden pr-5">
                  <swiper
                  @swiper="setSwiperA"
                  @slide-change="onSlideChangeA"
                  :effect="'cube'"
                    :grabCursor="true"
                    :cubeEffect="{
                      shadow: true,
                      slideShadows: true,
                      shadowOffset: 20,
                      shadowScale: 0.94,
                    }"
                    :modules="modules"
                    class="mySwiper"
                  >
                    <swiper-slide>Slide 1</swiper-slide>
                    <swiper-slide>Slide 2</swiper-slide>
                    <swiper-slide>Slide 3</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                    <swiper-slide>Slide 4</swiper-slide>
                  </swiper>
                </div>
              </div>
            </div>
        </div>
  </div>
  </template>
  <script>
    import Skills from './Skills.vue';
    // Import Swiper Vue.js components
    import { Swiper, SwiperSlide } from 'swiper/vue';
  
    // Import Swiper styles
    import 'swiper/css';
  
    import 'swiper/css/effect-cards';
  
    // import required modules
    import { EffectCube, Pagination } from 'swiper/modules';
  
    export default {
      components: {
        Swiper,
        SwiperSlide,
        Skills
      },
      setup() {
        return {
          activeIndex: 0, // ایندکس فعال مشترک
          swiperA: null, // نمونه Swiper کامپوننت A
          slidesA: ['Slide A1', 'Slide A2', 'Slide A3'],
          txt : [
            'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
            'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
            'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
            'کد نویسی فقط شغل من نیست، عشق منه!',
            'کد نویسی فقط شغل من نیست، عشق منه!',
            'کد نویسی فقط شغل من نیست، عشق منه!',
            'کد زدن برای من مثل حل کردن پازل هر روز زندگیه',
            'کد زدن برای من مثل حل کردن پازل هر روز زندگیه',
            'کد زدن برای من مثل حل کردن پازل هر روز زندگیه',
            'کد زدن برای من مثل حل کردن پازل هر روز زندگیه',
          ],
          modules: [EffectCube, Pagination],
        };
      },

      methods: {
        setSwiperA(swiper) {
          this.swiperA = swiper;
        },
        // هنگام تغییر اسلایدر A
        onSlideChangeA(swiper) {
          if (this.activeIndex !== swiper.activeIndex) {
            this.activeIndex = swiper.activeIndex;
          }
        },
        // دریافت تغییرات از کامپوننت B
        async onSlideChangeB(newIndex) {
          this.activeIndex = newIndex;
          if (this.swiperA && this.swiperA.activeIndex !== newIndex) {
            let x = 1;
            await this.swiperA.slideTo(newIndex);
            console.log(newIndex);
            console.log(this.swiperA.activeIndex);
          }
        },
      }
    };
  </script>
  

  <style scoped>
    
.swiper {
  width: 100%;
  height: 80vh !important;
  position: relative;
}

.swiper-slide {
  background: #040D12;
}
</style>