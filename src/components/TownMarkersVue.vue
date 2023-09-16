<template>
    <div class="TownMarkersVueComponent">
        <div class="CurrentLocationHourComponent">
            <h1>{{ now }}</h1>
        </div>
        <div class="FinanceCentersHourComponent">
            <div class="TownCardElement">
                <h1>Paris</h1>
                <ClockVue />
            </div>
            <div class="TownCardElement">
                <h1>New York</h1>
                <ClockVue />
            </div>
            <div class="TownCardElement">
                <h1>Tokyo</h1>
                <ClockVue/>
            </div>
        </div>
    </div>
</template>

<script>
import ClockVue from './ClockVue.vue';

export default {
    components: {
        ClockVue,
    },
    data() {
        return {
			towns : ["Paris","New York","Tokyo"],
            now: (new Date).getHours() +":"+(new Date).getMinutes() +":"+(new Date).getSeconds(),
			api_key:'d47a4adf9121f10b52f9d5f8adbfbee8',
			url_base:"https://api.openweathermap.org/data/2.5/",
			query:'',
			weather:{}
        };
    },
    computed() {
		return {
			localHours() {
				return (this.now).getHours() +":"+(this.now).getMinutes() +":"+(this.now).getSeconds();
			},
		}
    },
    created() {
        // Update the time every second
        setInterval(() => {
            this.now =  (new Date).getHours() +":"+(new Date).getMinutes() +":"+(new Date).getSeconds();
        }, 1000);
    },
    methods: {
        getLocalHours() {
            return this.localHours;
        },
    },
};
</script>

<style scoped>
.TownMarkersVueComponent {
    display: grid;
}
.CurrentLocationHourComponent {
    text-align: center;
}
.FinanceCentersHourComponent {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
.TownCardElement {
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
