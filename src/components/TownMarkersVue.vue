<template>
    <div class="TownMarkersVueComponent">
        <div class="CurrentLocationHourComponent">
            <h1>{{ now }}</h1>
        </div>
        <div class="FinanceCentersHourComponent">
            <div class="TownCardElement">
                <ClockVue TownName="New York"/>
            </div>
            <div class="TownCardElement">
                <ClockVue TownName="London"/>
            </div>
            <div class="TownCardElement">
                <ClockVue TownName="Paris"/>
            </div>

            <div class="TownCardElement">
                <ClockVue TownName="Tokyo"/>
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
            now: this.getLocalHours(),
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
            this.now = this.getLocalHours();
        }, 1000);
    },
    methods: {
        getLocalHours() {
            let hours     = ((new Date).getHours()>9) ? (new Date).getHours() : "0"+(new Date).getHours() ;
            let minutes   = ((new Date).getMinutes()>9) ? (new Date).getMinutes() : "0"+(new Date).getMinutes() ;
            let seconds   = ((new Date).getSeconds()>9) ? (new Date).getSeconds() : "0"+(new Date).getSeconds() ;

            return hours+":"+minutes +":"+seconds;
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
    box-shadow: 3px 3px 3px 2px rgba(255, 255, 255, 0.2);
}
</style>
