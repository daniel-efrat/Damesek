<template>
  <div>
    <Nav />
    <main>
      <article
        dir="rtl"
        class=" relative flex flex-col items-center"
      >
        <ClientOnly>
          <div
            id="song-page"
            class="relative w-screen h-full flex flex-col justify-center items-center"
          >
            <div id="bg" class="fixed w-screen h-screen ml-auto mr-auto inset-0">
				<img
              id="art"
              :src="blog.image"
              class="opacity-20 relative w-screen h-screen inset-0 mix-blend-multiply"
            />
			</div>

            

            <!-- audio player -->

            <div
              id="player"
              class="player w-full flex flex-col items-center relative mb-8 mt-8"
            >
              <label id="labelHe" class="text-3xl" for="audio">{{
                blog.title
              }}</label>
              <label id="labelEn" class="text-lg font-normal" for="audio"
                >{{ blog.titleEn }}
              </label>
              <audio controls :src="blog.audio"></audio>
            </div>
          </div>
          <ContentRenderer
            class="blog-link pr-7 max-w-none text-white"
            :value="blog"
          >
            <template #empty>
              <p>No content found.</p>
            </template>
          </ContentRenderer>
        </ClientOnly>
      </article>
    </main>
  </div>
</template>

<script setup>
const slug = useRoute().params.slug.toString().replace(/,/g, "/");
const { data: blog } = await useAsyncData(slug, () => {
  return queryContent(slug).findOne();
});

const toc = computed(() => {
  if (!blog.value) return [];
  const items = blog.value.excerpt?.children;
  if (!items) return [];
  const toc = [];
  const tags = ["h2", "h3", "h4", "h5", "h6"];
  items.forEach((item) => {
    if (tags.includes(item.tag)) {
      toc.push({
        id: item.props.id,
        title: item.props.id.toString().replace(/-/g, " "),
        depth: Number(item.tag.replace(/h/g, "")),
      });
    }
  });
  return toc;
});

useHead({
  title: `${blog.value.title}`,
});
</script>

<style>
#bg {
  z-index: 0;
  background: linear-gradient(118.74deg, rgba(255, 255, 255, 0.95) -9.92%, rgba(1, 55, 183, 0.95) 24.49%, rgba(0, 0, 0, 0.95) 54.61%, rgba(255, 0, 0, 0.95) 116.82%);
  background-position: center;
  background-repeat: no-repeat;
  z-index: 0;
}
#lyrics {
  font-family: "Times New Roman", Times, serif;
  font-size: 18px;
  background: rgba(0, 25, 100, 0.7);
  -webkit-backdrop-filter: blur(3px);
          backdrop-filter: blur(3px);
  width: 80vw;
}
@media only screen and (min-width: 600px) {
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

