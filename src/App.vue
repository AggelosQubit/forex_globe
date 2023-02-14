<template>
	<div>
		<h1 class="title1">
			Forex Clock
		</h1>
		<GlobeVue />
		<TownMarkersVue :scene="scene"/>

	</div>
</template>

<script>
	import GlobeVue from './components/GlobeVue.vue';
	import TownMarkersVue from './components/TownMarkersVue.vue';


	export default {
		components: {
			GlobeVue,
			TownMarkersVue
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
	body {
		margin: 0;
	}
	.title1{
		width: 100%;
		position: absolute;
		font-size: 4em;
		text-align: center;
		color: turquoise;
	}
	canvas {
	display: block;
	}
</style>