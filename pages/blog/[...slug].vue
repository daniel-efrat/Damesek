<template>
  <div>
    <Header />
    <main>
      <article dir="rtl" class="relative grid items-center justify-center">
        <ClientOnly>
          <div
            id="song-page"
            class="relative w-screen h-full flex flex-col justify-center items-center mt-14"
          >
            <div
              id="bg"
              class="fixed w-screen h-screen ml-auto mr-auto inset-0"
            >
              <img
                id="art"
                :src="songs.image"
                class="opacity-20 relative w-screen h-screen inset-0 mix-blend-multiply"
              />
            </div>

            <!-- audio player -->

            <div
              id="player"
              class="player w-full flex flex-col items-center relative mb-8 mt-8"
            >
              <label id="labelHe" class="text-3xl" for="audio">{{
                songs.title
              }}</label>
              <label id="labelEn" dir="ltr" class="text-lg font-normal" for="audio"
                >{{ songs.titleEn }}
              </label>
              <audio controls :src="songs.audio"></audio>
            </div>
         
          <ContentRenderer
            class="blog-link text-white relative ml-auto mr-auto grid items-center"
            :value="songs"
          >
            <template #empty>
              <p>No content found.</p>
            </template>
          </ContentRenderer>
           </div>
        </ClientOnly>
      </article>
    </main>
  </div>
</template>

<script setup>
const slug = useRoute().params.slug.toString().replace(/,/g, "/");
const { data: songs } = await useAsyncData(slug, () => {
  return queryContent(slug).findOne();
});


useHead({
  title: `${songs.value.title}`,
});
</script>

<style>
#bg {
  z-index: 0;
  background: linear-gradient(
    118.74deg,
    rgba(255, 255, 255, 0.95) -9.92%,
    rgba(1, 55, 183, 0.95) 24.49%,
    rgba(0, 0, 0, 0.95) 54.61%,
    rgba(255, 0, 0, 0.95) 116.82%
  );
  background-position: center;
  background-repeat: no-repeat;
  z-index: 0;
}
#lyrics {
  background: rgba(0, 25, 100, 0.7);
  -webkit-backdrop-filter: blur(3px);
  backdrop-filter: blur(3px);
  width: 90vw;
}
@media (min-width: 600px) {
  #lyrics {
    font-size: 19px;
    width: 80vw;
  }
}
@media (min-width: 1000px) {
  #lyrics {
    font-size: 19px;
    width: 60vw;
  }
}

nuxt-link {
  text-decoration: none;
}
.page-enter-active,
.page-leave-active {
  transition: opacity 0.5s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>
