<template>
  <div id="lyrics" class="relative z-30 rounded-xl p-3 shadow-2xl md:p-12">
    <img class="thumbnail mt-4 mb-4" src="/images/trust.png" alt="" />
  </div>
</template>
<script>
export default {
  layout: "song",
};
</script>
<style>
* {
  font-family: "Times New Roman", Times, serif;
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
