<template>
    <div class="TownMarkersVueComponent"> 
		<div class="CurrentLocationHourComponent">
			<h1>{{ localHours }}</h1>
		</div>
		<div class="FinanceCentersHourComponent">
			<div class="TownCardElement">
				<h1>Paris</h1>
				<ClockVue />
				<h2>{{ localHours }}</h2>
			</div>
			<div class="TownCardElement">
				<h1>New York</h1>
				<ClockVue />
				<h2>{{ localHours }}</h2>
			</div>
			<div class="TownCardElement">
				<h1>Tokyo</h1>
				<ClockVue  />
				<h2>{{ localHours }}</h2>
			</div>
		</div>
	</div>
</template>

<script>
	import ClockVue from './ClockVue.vue';

	export default {
		components:{
			ClockVue,
		},
		props:{
			localHours:String
		}
		,data() {
			return {
				scene: null
			};
		},
		created() {

		},
		methods() {
		}
	};
</script>
<style scoped>
.TownMarkersVueComponent{
	display: grid;
}
.CurrentLocationHourComponent{
	text-align: center;
}
.FinanceCentersHourComponent{
	display: flex;
	flex-direction: row;
	justify-content: space-around;
}
.TownCardElement{
	color: wheat;
    background-color: rgb(32, 32, 32);
    height: 350px;
    border-radius: 8px;
    margin-bottom: 50px;
    width: 270px;
    text-align: center;
    box-shadow: 3px 3px 3px 2px rgba(0, 0, 0, 0.2);
}
</style>