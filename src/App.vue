<template>
		<h1 class="title1">
			Forex Clock
		</h1>
		<GlobeVue />
		<PlayerVue />
</template>

<script>
	import GlobeVue from './components/GlobeVue.vue';
	import PlayerVue from './components/PlayerVue.vue';
	export default {
		components: {
			GlobeVue,
			PlayerVue
			
		}, 
		mounted() {
			this.$nextTick(
				() => {
					this.$refs.townMarkers.setScene(this.$refs.globe.scene);
				}
			);
		}
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
	}
	canvas {
		position: fixed;
		top: 0%;
		left: 0%;
	}
</style>