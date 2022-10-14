<template>
	<div class="min-h-screen">
		<Nav />
		<main dir="rtl" >
			<section class="lg:px-[15%] px-[5%] pt-20">
			
			</section>
			<section class="lg:px-[15%] px-[5%] lg:pt-20 pt-14">
			
				<div class="grid grid-cols-1 gap-4">
					<template
						v-for="(b, i) in blogNav[0].children"
						:key="`blogNavItem-${b._path}-${i}`"
					>
						<div class="px-7 py-5 rounded-lg border-2">
						
							<ul class="list-disc list-inside mt-4 pl-2 space-y-3">
								<li
									class="list-item text-sm text-gray-200 hover:text-primary-900 transition-all"
								>
									<NuxtLink :to="`/blog${b._path}`"> {{b.title}} </NuxtLink>
								</li>
							</ul>
						</div>
					</template>
				</div>
			</section>
			<div class="box w-20 h-20 bg-violet-500">box</div>
		</main>
	</div>
</template>

<script setup>

	const { data: blogNav } = await useAsyncData("navigation", () => {
		return fetchContentNavigation(queryContent("blog"));
	});
	useHead({
		title: "Content Blog",
	});
</script>
<script>
import gsap from 'gsap'

export default {
mounted(){
	gsap.to('.box', {x:-500})
}

}
</script>
