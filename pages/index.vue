<template>
  <div
    class="relative grid h-screen w-screen items-center justify-center overflow-hidden"
  >
    <div id="bg" class="fixed inset-0 ml-auto mr-auto h-screen w-screen"></div>
    <div id="bg2" class="fixed inset-0 ml-auto mr-auto h-screen w-screen"></div>

    <!-- video & button -->

    <div class="relative mt-32 flex flex-col items-center justify-center">
      <video muted autoplay src="/images/logoAnim.mp4" id="vid"></video>
      <button
        @click="drop"
        id="enter"
        class="relative mt-20 w-max rounded-full bg-white px-4 py-2 font-bold text-blue-700 shadow-md transition-all hover:bg-orange-400 hover:text-white hover:shadow-2xl"
      >
        כניסה
      </button>
    </div>

    <!-- images -->

    <div class="images grid">
      <div class="eli absolute inset-0 h-screen w-screen mix-blend-difference">
        <img
          class="desktop inset-0 mr-auto ml-auto mb-auto"
          src="/images/eli.png"
          alt=""
        />
        <img
          class="mobile inset-0 mr-auto ml-auto"
          src="/images/eli-mobile.png"
          alt=""
        />
      </div>

      <div
        class="square absolute inset-0 h-screen w-screen mix-blend-difference"
      >
        <img
          class="desktop inset-0 mr-auto ml-auto mb-auto"
          src="/images/square.png"
          alt=""
        />
        <img
          class="mobile inset-0 mr-auto ml-auto mb-auto"
          src="/images/square-mobile.png"
          alt=""
        />
      </div>
    </div>

    <div
      class="list1 fixed top-0 right-0 left-0 bottom-0 mr-auto ml-auto grid h-screen w-screen items-start mt-8 justify-center"
    >
      <div dir="rtl">
        <div class="relative grid grid-cols-1 -mt-20 sm:mt-auto gap-1">
          <h2 class="text-center text-2xl">שירים</h2>
          <template
          v-for="(b, i) in blogNav[0].children"
          :key="`blogNavItem-${b._path}-${i}`"
          >
            <ol class="list-inside list-none">
              <li class="list-item">
                <NuxtLink :to="`/blog${b._path}`"> {{ b.title }} </NuxtLink>
              </li>
            </ol>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const { data: blogNav } = await useAsyncData("navigation", () => {
  return fetchContentNavigation(queryContent("blog"));
});
</script>
<script>
import gsap from "gsap";
definePageMeta({
  pageTransition: {
    mode: "default",
    appear: true,
  },
});
export default {
  mounted() {
    gsap.set(".square", { x: "50vw"});
    gsap.set(".eli", { x: "-50vw"});
    gsap.set("#enter", { opacity:0});

    gsap.to('#bg2', {opacity:0})
    gsap.to('#bg2', {y:'-100vh', delay:.5})

    gsap.to(".square", { x: 0, opacity: 0.7, duration: 6 });
    gsap.to(".eli", { x: 0, opacity: 0.2, duration: 6 });

    gsap.to("#enter", {  opacity:1});
  },
  methods: {
    drop() {
      gsap.to(".list1", { y: 0, duration: 1 });
      gsap.to("#vid", { opacity: 0 });
      gsap.to("#enter", { opacity: 0 });
      gsap.to(".square", { x: 0, opacity: 0.2, duration: 1 });
      gsap.to(".eli", { x: 0, opacity: 0.1, duration: 1 });
    },
  },
};
</script>

<style scoped>
#bg2 {
  background: linear-gradient(118.74deg, rgba(255, 255, 255, 1) -9.92%, rgba(1, 55, 183, 1) 24.49%, rgba(0, 0, 0, 1) 54.61%, rgba(255, 0, 0, 1) 116.82%);
  background-position: center;
  background-repeat: no-repeat;
  z-index: 51;
}
video {
  position: relative;
  z-index: 2;
  mix-blend-mode: screen;
}

.list1 {
  transform: translateY(-125vh);
  z-index: 5000;
}
.eli {
  opacity:0
}
.square{
  opacity:0
}
#enter {
  z-index: 50;
}
img {
  position: absolute;
  mix-blend-mode: color-dodge;
  z-index: 1;
  width: 100%;
}
@media screen and (max-width: 400px) {
  .desktop {
    display: none;
  }
}
@media (max-width: 600px) {
  .desktop {
    display: none;
  }
}
@media (min-width: 600px) {
  .mobile {
    display: none;
  }
}
@media (min-width: 1000px) {
  img {
    transform: scale(0.7);
    margin-top: -200px;
  }
  .eli {
    margin-left: -150px;
  }
  .square {
    margin-left: 200px;
  }
}

</style>
