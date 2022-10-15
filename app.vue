<template>
	<div class="bg-gray-900 text-gray-200 min-h-screen">
		<NuxtPage />
	</div>
</template>
<script>

</script>
<style>
#bg {
  background: linear-gradient(118.74deg, rgba(255, 255, 255, 0.95) -9.92%, rgba(1, 55, 183, 0.95) 24.49%, rgba(0, 0, 0, 0.95) 54.61%, rgba(255, 0, 0, 0.95) 116.82%);
  background-position: center;
  background-repeat: no-repeat;
  z-index: 0;
}
.list {
  transform: translateY(-125vh);
  z-index: 5000;
  background: linear-gradient(
    118.74deg,
    rgba(255, 255, 255, 0.85) -9.92%,
    rgba(1, 55, 183, 0.85) 24.49%,
    rgba(0, 0, 0, 0.85) 54.61%,
    rgba(255, 0, 0, 0.85) 116.82%
  );
  background-position: center;
  background-repeat: no-repeat;
  backdrop-filter: blur(5px);
}
#dropDown {
  z-index: 5000;
  font-family: "Heebo", sans-serif;
  width: max-content;
  height: max-content;
  padding-bottom: 40px;
  padding-top: 10px;
  padding-right: 60px;
  padding-left: 60px;
  border-radius: 20px;
}
.list-item, h2 {
  text-shadow: 2px 2px 2px black;
  border-bottom: 1px solid white;
  padding-bottom: 10px;
  padding-top: 10px;
  font-size: 16pt;
}
@media (max-width: 600px) {
  #dropDown {
    width: 100vw;
    height: 100vh;
    margin-top: 60px;
  }
  .list-item {
  padding-bottom: 5px;
  padding-top: 5px;
  font-size: 14pt;
}
}
.page-enter-active,
.page-leave-active {
  transition: opacity 0.7s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>