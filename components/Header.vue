<template>
  <div class="relative">
    <!-- component -->
    <nav
      id="header"
      class="w-full flex justify-center fixed z-30 top-0 border-b border-blue-400 shadow-2xl"
    >
      <div
        id="navbar"
        class="w-4/5 lg:w-3/5 flex relative items-center justify-between mt-0 px-6"
      >
        <!-- icons -->
        <div class="icons relative flex mt-7 -ml-2">
          <nuxt-link
            class="icon gallery relative"
            to="/gallery"
            @click="refresh"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="w-6 h-6 mt-3 hover:fill-orange-400"
            >
              <path
                fill-rule="evenodd"
                d="M1.5 6a2.25 2.25 0 012.25-2.25h16.5A2.25 2.25 0 0122.5 6v12a2.25 2.25 0 01-2.25 2.25H3.75A2.25 2.25 0 011.5 18V6zM3 16.06V18c0 .414.336.75.75.75h16.5A.75.75 0 0021 18v-1.94l-2.69-2.689a1.5 1.5 0 00-2.12 0l-.88.879.97.97a.75.75 0 11-1.06 1.06l-5.16-5.159a1.5 1.5 0 00-2.12 0L3 16.061zm10.125-7.81a1.125 1.125 0 112.25 0 1.125 1.125 0 01-2.25 0z"
                clip-rule="evenodd"
              />
            </svg>
          </nuxt-link>

          <nuxt-link class="icon home relative -ml-10" to="/" @click="refresh">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="w-6 h-6 mt-2 hover:fill-orange-400"
              ref="homeIcon"
            >
              <path
                d="M11.47 3.84a.75.75 0 011.06 0l8.69 8.69a.75.75 0 101.06-1.06l-8.689-8.69a2.25 2.25 0 00-3.182 0l-8.69 8.69a.75.75 0 001.061 1.06l8.69-8.69z"
              />
              <path
                d="M12 5.432l8.159 8.159c.03.03.06.058.091.086v6.198c0 1.035-.84 1.875-1.875 1.875H15a.75.75 0 01-.75-.75v-4.5a.75.75 0 00-.75-.75h-3a.75.75 0 00-.75.75V21a.75.75 0 01-.75.75H5.625a1.875 1.875 0 01-1.875-1.875v-6.198a2.29 2.29 0 00.091-.086L12 5.43z"
              />
            </svg>
          </nuxt-link>
        </div>
        <!-- links dropdown -->
        <div
          id="button"
          class="text-base absolute left-0 right-0 p-2 mr-auto -ml-6 cursor-pointer grid items-center justify-center"
        >
          <div
            id="shirim"
            ref="shirim"
            @mouseover="shirimHover"
            @mouseleave="shirimLeave"
            @click="drop"
            class="cursor-pointer text-center flex"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="w-4 h-4 mr-1 mt-1"
              ref="down"
            >
              <path
                fillRule="evenodd"
                d="M20.03 4.72a.75.75 0 010 1.06l-7.5 7.5a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 011.06-1.06L12 11.69l6.97-6.97a.75.75 0 011.06 0zm0 6a.75.75 0 010 1.06l-7.5 7.5a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 111.06-1.06L12 17.69l6.97-6.97a.75.75 0 011.06 0z"
                clipRule="evenodd"
              />
            </svg>

            <p class="" ref="pShirim">כל השירים</p>
          </div>

          <div
            @mouseover="sgiraHover"
            @mouseleave="sgiraLeave"
            @click="rollup"
            class="cursor-pointer text-center hidden"
            id="sgira"
            ref="sgira"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="up w-4 h-4 mr-1 mt-1"
              ref="up"
            >
              <path
                fillRule="evenodd"
                d="M11.47 4.72a.75.75 0 011.06 0l7.5 7.5a.75.75 0 11-1.06 1.06L12 6.31l-6.97 6.97a.75.75 0 01-1.06-1.06l7.5-7.5zm.53 7.59l-6.97 6.97a.75.75 0 01-1.06-1.06l7.5-7.5a.75.75 0 011.06 0l7.5 7.5a.75.75 0 11-1.06 1.06L12 12.31z"
                clipRule="evenodd"
              />
            </svg>

            <p
              class=""
              ref="pSgira"
            >
              סגירה
            </p>
          </div>
        </div>
        <!-- logo -->
        <Logo-o class="w-20 relative sm:w-24 -mr-12 mt-2" />
      </div>
    </nav>
    <!-- actual dropdown -->
    <div
      class="list fixed w-screen h-screen mr-auto ml-auto pt-10 top-0 right-0 left-0 bottom-0 sm:mt-auto grid items-center justify-center"
    >
      <div
        dir="rtl"
      >
			
				<div class="grid grid-cols-1 gap-1 relative ">
          <h2 class="text-center text-2xl">שירים</h2>

					<template
						v-for="(b, i) in blogNav[0].children"
						:key="`blogNavItem-${b._path}-${i}`"
					>
							<ol class="list-none">
								<li
									class="list-item"
								>
									<NuxtLink :to="`/blog${b._path}`" class="hover:text-orange-400"> {{b.title}} </NuxtLink>
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
import gsap from 'gsap'
export default {
  data() {
    return {
      hidden: true,
    };
  },

  methods: {
    shirimHover() {
      this.$refs.down.classList.add("fill-orange-400");
      this.$refs.pShirim.classList.add("orange");
    },
    shirimLeave() {
      this.$refs.down.classList.remove("fill-orange-400");
      this.$refs.pShirim.classList.remove("orange");
    },
    sgiraHover() {
      this.$refs.up.classList.add("fill-orange-400");
      this.$refs.pSgira.classList.add("orange");
    },
    sgiraLeave() {
      this.$refs.up.classList.remove("fill-orange-400");
      this.$refs.pSgira.classList.remove("orange");
    },

    drop() {
      this.$refs.sgira.classList.remove("hidden");
      this.$refs.sgira.classList.add("flex");
      this.$refs.shirim.classList.add("hidden");

      gsap.to(".list", { y: 0, duration: 1 });
    },
    rollup() {
      this.$refs.shirim.classList.remove("hidden");
      this.$refs.sgira.classList.add("hidden");

      gsap.to(".list", { y: "-125vh", duration: 1 });
    },
    refresh() {
      const newPage = this.$nuxt.refresh();
      setTimeout(newPage, 1500);
    },
  },
};
</script>
<style lang="scss"
scoped>
* {
	color: white;
}
nav {
	background: linear-gradient(
    118.74deg,
    rgba(255, 255, 255, 0.95) -9.92%,
    rgba(1, 55, 183, 0.95) 24.49%,
    rgba(0, 0, 0, 0.95) 54.61%,
    rgba(255, 0, 0, 0.95) 116.82%
  );
	background-position: center;
	background-repeat: no-repeat;
	z-index: 5001;
}
#shirim,
#sgira {
	position: relative;
	border-bottom: 2px white solid;
	padding-bottom: 0;
	padding-right: 2px;
	padding-left: 0px;
	margin-left: 25px;
	font-size: 14px;
	font-family: "Heebo", sans-serif;
}
#shirim:hover,
#sgira:hover {
	border-color: #ffa500;
}
.orange {
	color: #ffa500;
}

.icon {
	position: relative;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	width: 100%;
	height: 100%;
	fill: none;
	stroke-width: 6;
	stroke-linecap: round;
	stroke-linejoin: round;
	cursor: pointer;
	z-index: 5000;
}

</style>
