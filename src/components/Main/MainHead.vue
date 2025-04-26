<template>
    <div class="w-full h-full bg-[url(/src/assets/images/head_1.jpg)] bg-no-repeat bg-cover relative">
        <div class="absolute top-0 left-0 w-full h-full opacity-90 bg-lux-green-1"></div>
        <div class="absolute top-0 left-0 w-full h-full p-5">
            <div class="p-5 border border-lux-green-2 rounded-xl w-full h-full flex items-center justify-center">
                <div class="absolute bottom-[-30px] left-[-30px] md:w-[350px] w-[200px] scale-x-[-1]">
                    <img src="../../assets/images/head_inside_1.png"  ref="movingElement" class=" moving-element from-bottom-right" alt="">
                </div>
                <div class="flex md:flex-row flex-col items-center justify-center md:gap-10 gap-5">
                    <div class="flex md:flex-col flex-row gap-5">
                        <div class="from-right border-lux-green-2 bg-transparent border duration-150 hover:bg-lux-green-2 cursor-pointer rounded-full md:h-10 md:w-10 w-7 h-7"></div>
                        <div class="from-right delay-02 border-lux-green-2 bg-transparent border duration-150 hover:bg-lux-green-2 cursor-pointer rounded-full md:h-10 md:w-10 w-7 h-7"></div>
                        <div class="from-right delay-04 border-lux-green-2 bg-transparent border duration-150 hover:bg-lux-green-2 cursor-pointer rounded-full md:h-10 md:w-10 w-7 h-7"></div>
                        <div class="from-right delay-06 border-lux-green-2 bg-transparent border duration-150 hover:bg-lux-green-2 cursor-pointer rounded-full md:h-10 md:w-10 w-7 h-7"></div>
                    </div>
                    
                    <div>
                        <div class="from-top-right overflow-hidden md:w-[350px] md:h-[450px] w-[200px] h-[250px] p-10 bg-lux-green-1 rounded-full relative">
                            
                        </div>
                    </div>
                    <div>
                        
                        <div class="md:text-right text-center md:w-full w-[250px] leading-10">
                            <h1 class="top-opacity md:text-4xl text-2xl yekan-bold mb-3">سلام! من یوسفم</h1>
                            <div class="md:w-[650px]">
                                <q id="demo" class="top-opacity delay-06 md:text-xl text-sm text-lux-green-4">{{ txt[getRandomNumber(1, 10)] }}</q>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const getRandomNumber = (min, max) => {
  return Math.floor(Math.random() * (max - min) + min);
}

let txt = [
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'کد نویسی فقط شغل من نیست، عشق منه!',
    'کد زدن برای من مثل حل کردن پازل هر روز زندگیه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
    'یه موجود دیجیتال که روز ها کدنویسی میکنه و شب ها باگ ها رو تو خواب میبینه',
];

const movingElement = ref(null); // ایجاد رف برای المان
const sensitivity = 0.03;
let mouseX = 0;
let mouseY = 0;

// تنظیم event listener برای موس
const handleMouseMove = (e) => {
  mouseX = e.clientX;
  mouseY = e.clientY;
};

onMounted(() => {
    window.addEventListener('mousemove', handleMouseMove);
    updatePosition();
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove);
});

const updatePosition = () => {
  if (!movingElement.value) return; // بررسی وجود المان

  const centerX = window.innerWidth / 2;
  const centerY = window.innerHeight / 2;
  const moveX = (mouseX - centerX) * -sensitivity;
  const moveY = (mouseY - centerY) * -sensitivity;

  movingElement.value.style.transform = `translate(${moveX}px, ${moveY}px)`;
  
  requestAnimationFrame(updatePosition);
};
</script>

<style scoped>
.moving-element{
    transition: transform 0.3s ease-out;
}
.from-top-right{
    position: relative;
    animation-name: topRight;
    animation-fill-mode: backwards;
    animation-duration: 1s;
}

.from-top-left{
    position: relative;
    animation-name: topLeft;
    animation-fill-mode: backwards;
    animation-duration: 1s;
}

.from-bottom-left{
    position: relative;
    animation-name: BottomLeft;
    animation-fill-mode: backwards;
    animation-duration: 1s;
}

.from-bottom-right{
    position: relative;
    animation-name: BottomRight;
    animation-duration: 1s;
    animation-fill-mode: backwards;
}

.from-right{
    position: relative;
    animation-name: FromRight;
    animation-duration: 1s;
    animation-fill-mode: backwards;
}

.top-opacity{
    position: relative;
    animation-name: topOpacity;
    animation-timing-function: linear;
    animation-duration: 500ms;
    animation-fill-mode: backwards;
}

.delay-1{
    animation-delay: 1s;
}

.delay-02{
    animation-delay: 0.2s;
}

.delay-04{
    animation-delay: 0.4s;
}

.delay-06{
    animation-delay: 0.6s;
}

.delay-08{
    animation-delay: 0.8s;
}

@keyframes topRight {
    from {top: -700px; left: 700px; opacity: 0}
    to {top: 0px; left: 0; opacity: 1}
}


@keyframes FromRight {
    from {left: 700px; opacity: 0}
    to {left: 0; opacity: 1}
}


@keyframes topLeft {
    from {top: -700px; right: 700px; opacity: 0}
    to {top: 0px; right: 0; opacity: 1}
}
@keyframes BottomRight {
    from {bottom: -700px; left: 700px; opacity: 0}
    to {bottom: 0px; left: 0; opacity: 1}
}
@keyframes BottomLeft {
    from {bottom: -700px; right: 700px; opacity: 0}
    to {bottom: 0px; right: 0; opacity: 1}
}

@keyframes topOpacity {
    from {top: -30px; opacity: 0}
    to {top: 0px; opacity: 1}
}
</style>