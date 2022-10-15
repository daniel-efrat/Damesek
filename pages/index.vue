<template>
  <div class="w-screen h-screen grid items-center justify-center relative">
    <!-- <div ref="header" class="header absolute"><Header /></div> -->

    <div id="bg" class="fixed w-screen h-screen ml-auto mr-auto inset-0"></div>
    <div class="flex flex-col items-center absolute">
      <video muted autoplay src="/images/logoAnim.mp4"></video>
      <!-- <nuxt-link to="/menu"> -->
      <button
        @click="drop"
        id="enter"
        class="text-blue-700 font-bold bg-white w-max px-4 py-2 rounded-full transition-all hover:bg-orange-400 hover:text-white shadow-md hover:shadow-2xl relative"
      >
        כניסה
      </button>
      <!-- </nuxt-link> -->

      <div class="images w-screen h-screen fixed">
        <img class="eli relative -mt-80" src="/images/eli.png" alt="" />
        <img class="square relative -mt-60" src="/images/square.png" alt="" />
      </div>
      <div
        class="list fixed w-screen h-screen mr-auto ml-auto top-0 right-0 left-0 bottom-0 grid items-center justify-center"
      >
        <div dir="rtl">
          <div class="grid grid-cols-1 gap-1 relative">
            <template
              v-for="(b, i) in blogNav[0].children"
              :key="`blogNavItem-${b._path}-${i}`"
            >
              <ol class="list-none list-inside pl-2">
                <li class="list-item text-sm text-gray-200 transition-all">
                  <NuxtLink :to="`/blog${b._path}`"> {{ b.title }} </NuxtLink>
                </li>
              </ol>
            </template>
          </div>
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
export default {
  mounted() {
    gsap.set(".square", { x: "50vw", opacity: 0 });
    gsap.set(".eli", { x: "-50vw", opacity: 0 });
    gsap.set("#enter", { opacity: 0 });
    gsap.set(".logo", { opacity: 0 });
    gsap.set("#list", { y: "-100vh" });
    gsap.set(".header", { opacity: 0 });

    gsap.to(".square", { x: 0, opacity: 0.7, duration: 6 });
    gsap.to(".eli", { x: 0, opacity: 0.2, duration: 6 });

    gsap.to("#enter", { opacity: 1, duration: 0.5, delay: 2.5 });
  },
  methods: {
    drop() {
       gsap.to(".list", { y: 0, duration: 1 });
    },
  },
};
</script>

<style scoped>
video {
  position: relative;
  z-index: 2;
  mix-blend-mode: screen;
}
button {
  z-index: 50;
}

img {
  position: absolute;
  mix-blend-mode: color-dodge;
  z-index: 1;
  width: 100%;
  opacity: 0.2;
}

</style>
