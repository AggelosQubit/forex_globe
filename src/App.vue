<template>
		<h1 class="title1">
			Forex Clock
		</h1>
		<GlobeVue />
		<PairsVue />
		<PlayerVue />
</template>

<script>
	import GlobeVue from './components/GlobeVue.vue';
	import PlayerVue from './components/PlayerVue.vue';
	import PairsVue from './components/PairsVue.vue';
	
	export default {
		components: {
			GlobeVue,
			PlayerVue,
			PairsVue,
			
		},
	};
</script>

<style>
	.title1{
		position: relative;
		width: 100%;
		font-size: 4em;
		text-align: center;
		color: turquoise;
		margin: 0;
		z-index: 1;
		text-shadow : 3px 3px 3px wheat;
	}
	canvas {
		position: fixed;
		top: 0%;
		left: 0%;
	}
</style>