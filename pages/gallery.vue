<template>
  <div>
    <Header/>
    <div
      id="song-page"
      class="relative w-screen h-full flex flex-col items-center mt-16 mb-10 -ml-1"
    >
      <div id="bg" class="fixed w-screen h-screen top-0 z-0"></div>

      <container
        class="titles w-screen h-fit m-4 relative flex flex-col items-center"
      >
        <h1 class="galeria text-white text-4xl font-bold" dir="rtl">גלריה</h1>
        <p dir="rtl" class="text-sm text-white mb-6">
          כל הציורים באתר נוצרו בעזרת
          <a
            class="underline underline-offset-3 text-md cursor-pointer text-orange"
            dir="ltr"
            href="https://openai.com/dall-e-2"
            >DALL-E 2
          </a>
        </p>
      </container>

      <div class="gallery relative w-4/5 md:w-3/5 grid gap-10 sm:gap-6 mx-auto">
        <!-- images -->
        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/morning.png" alt="כיכר מרגה סבאח אל ח'יר" />
          <label class="mt-1" for="">כיכר מרגה סבאח אל ח'יר</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/speck.png" alt="" />
          <label class="mt-1" for="">גרגר אבק</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/hafez.png" alt="פרויקט חַאפֵז" />
          <label class="mt-1" for="">פרויקט חַאפֵז</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/peace.png" alt="כל העולם סלאם" />
          <label class="mt-1" for="">כל העולם סלאם</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/trust.png" alt="אדם לאדם זאב" />
          <label class="mt-1" for="">אדם לאדם זאב</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/who.png" alt="מי אתה?" />
          <label dir="rtl" class="mt-1" for="">מי אתה?</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/bing.png" alt="בינג - Voilà" />
          <label class="mt-1" for=""><span>Voilà - </span>בינג</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/center.png" alt="מרכז העולם" />
          <label class="mt-1" for="">מרכז העולם</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/letters.png" alt="מכתבים" />
          <label class="mt-1" for="">מכתבים</label>
        </div>

        <div
          class="image w-full flex flex-col items-center rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/i-am.png" alt="איש אחד" />
          <label class="mt-1" for="">איש אחד</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
       >
          <img src="/images/spy1.png" alt="מרגל בדמשק" />
          <label class="mt-1" for="">מרגל בדמשק 1</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/spy2.png" alt="מרגל בדמשק" />
          <label class="mt-1" for="">מרגל בדמשק 2</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/spy3.png" alt="מרגל בדמשק" />
          <label class="mt-1" for="">מרגל בדמשק 3</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500"
        >
          <img src="/images/spy4.png" alt="מרגל בדמשק" />
          <label class="mt-1" for="">מרגל בדמשק 4</label>
        </div>

        <div
          class="image flex flex-col items-center w-full rounded opacity-80 hover:opacity-100 transition ease-in-out duration-500 mb-20"
        >
          <img src="/images/spy5.png" alt="מרגל בדמשק" />
          <label class="mt-1" for="">מרגל בדמשק 5</label> 
        </div>
      </div>
    </div>
  </div>
</template>

<script>

</script>

<style scoped>
* {
  font-family: "Heebo", sans-serif;
  color: white;
}
.galeria {
  text-shadow: 2px 2px 2px black;
  border-bottom: 2px white solid;
  margin-bottom: 15px;
}
a {
  color: orange;
}
.image {
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.451);
}
.image:hover {
  box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.425);
  transform: scale(1.2);
  z-index: 5;
}
.page-enter-active,
.page-leave-active {
  transition: opacity 0.5s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
@media (min-width: 450px) {
  .gallery {
    grid-template-columns: 1fr 1fr;
  }
}
@media (min-width: 800px) {
  .gallery {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
@media (min-width: 1000px) {
  .gallery {
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}
</style>
