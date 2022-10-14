<template>
 
        <div
          id="lyrics"
          class="p-5 md:p-12 rounded-xl shadow-2xl z-30 relative"
        >
      
      
      <img class="thumbnail mt-4 mb-4" src="/images/trust.png" alt=""/>
      </div>
  
</template>
<script>
export default {
  layout: 'song',
}
</script>
<style>
* {
  font-family: 'Times New Roman', Times, serif;
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
