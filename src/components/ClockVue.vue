<template>
    <h1 class="ClockVueTownComponent">{{ TownName }}</h1>
    <div class="ClockVueComponent">
        <svg version="1.1" :class="TownName" x="0px" y="0px" width="150px" height="150px" viewBox="0 0 384 384"
            enable-background="new 0 0 384 384" xml:space="preserve">
            <path :class=classHtml[0] fill="#B3CAF5"
                d="M192,0C85.961,0,0,85.961,0,192s85.961,192,192,192s192-85.961,192-192S298.039,0,192,0zM315.037,315.037c-9.454,9.454-19.809,17.679-30.864,24.609l-14.976-25.939l-10.396,6l14.989,25.964c-23.156,12.363-48.947,19.312-75.792,20.216V336h-12v29.887c-26.845-0.903-52.636-7.854-75.793-20.217l14.989-25.963l-10.393-6l-14.976,25.938c-11.055-6.931-21.41-15.154-30.864-24.608s-17.679-19.809-24.61-30.864l25.939-14.976l-6-10.396l-25.961,14.99C25.966,250.637,19.017,224.846,18.113,198H48v-12H18.113c0.904-26.844,7.853-52.634,20.216-75.791l25.96,14.988l6.004-10.395L44.354,99.827c6.931-11.055,15.156-21.41,24.61-30.864s19.809-17.679,30.864-24.61l14.976,25.939l10.395-6L110.208,38.33C133.365,25.966,159.155,19.017,186,18.113V48h12V18.113c26.846,0.904,52.635,7.853,75.792,20.216l-14.991,25.965l10.395,6l14.978-25.942c11.056,6.931,21.41,15.156,30.865,24.611c9.454,9.454,17.679,19.808,24.608,30.863l-25.94,14.976l6,10.396l25.965-14.99c12.363,23.157,19.312,48.948,20.218,75.792H336v12h29.887c-0.904,26.845-7.853,52.636-20.216,75.792l-25.964-14.989l-6.002,10.396l25.941,14.978C332.715,295.229,324.491,305.583,315.037,315.037z" />
            <line :class=classHtml[1] :id=classHtml[7] fill="none" stroke="#B3CAF5" stroke-width="18"
                stroke-miterlimit="10" x1="192" y1="192" x2="192" y2="87.5" />
            <line :class=classHtml[2] :id=classHtml[8] fill="none" stroke="#B3CAF5" stroke-width="12"
                stroke-miterlimit="10" x1="192" y1="192" x2="192" y2="54" />
            <circle :class=classHtml[3] cx="192" cy="192" r="9" />
            <g :class=classHtml[4] :id="classHtml[9]">
                <line :class=classHtml[5] fill="none" stroke="#D53A1F" stroke-width="4" stroke-miterlimit="10" x1="192"
                    y1="192" x2="192" y2="28.5" />
                <circle :class=classHtml[6] fill="#D53A1F" cx="192" cy="192" r="4.5" />
            </g>
            <defs>
                <animateTransform type="rotate" fill="remove" restart="always" calcMode="linear" accumulate="none"
                    additive="sum" :xlink:href=classHtml[7] repeatCount="indefinite" dur="43200s" to="360 192 192"
                    from="0 192 192" attributeName="transform" attributeType="xml">
                </animateTransform>

                <animateTransform type="rotate" fill="remove" restart="always" calcMode="linear" accumulate="none"
                    additive="sum" :xlink:href=classHtml[8] repeatCount="indefinite" dur="3600s" to="360 192 192"
                    from="0 192 192" attributeName="transform" attributeType="xml">
                </animateTransform>

                <animateTransform type="rotate" fill="remove" restart="always" calcMode="linear" accumulate="none"
                    additive="sum" :xlink:href=classHtml[9] repeatCount="indefinite" dur="60s" to="360 192 192"
                    from="0 192 192" attributeName="transform" attributeType="xml">
                </animateTransform>
            </defs>
        </svg>
        <h2 class="ClockVueHourComponent">{{ now }}</h2>
    </div>
</template>
<script>
export default {
    data() {
        return {
            api_key: "d47a4adf9121f10b52f9d5f8adbfbee8",
            url_base: "https://api.openweathermap.org/data/2.5/",
            query: "",
            weather: {},
            now: this.getLocalHours(),
            now_utcc: Number,
            classHtml: []
        }
    },
    props: {
        TownName: String,
    },
    created() {
        this.setClassHtml();
        fetch(`${this.url_base}weather?q=${this.TownName}&units=metric&APPID=${this.api_key}`)
            .then(response => {
                return response.json()
            }).then(this.setResult)
        //console.log(this.weather)
        setInterval(
            () => {
                //console.log("setInterval");
                this.now_utcc = this.now_utcc + 1000;
                this.now = this.getLocalHours();
            }, 1000);
    },
    methods: {
        setClassHtml() {
            this.classHtml.push(this.TownName + "-frame");
            this.classHtml.push(this.TownName + "-hour-hand");
            this.classHtml.push(this.TownName + "-minute-hand");
            this.classHtml.push(this.TownName + "-axis");
            this.classHtml.push(this.TownName + "-second-hand");
            this.classHtml.push(this.TownName + "-second-hand-arm");
            this.classHtml.push(this.TownName + "-second-hand-axis");
            this.classHtml.push("#iconic-anim-clock-hour-hand-" + this.TownName)
            this.classHtml.push("#iconic-anim-clock-minute-hand-" + this.TownName)
            this.classHtml.push("#iconic-anim-clock-second-hand-" + this.TownName)
        },
        setResult(results) {
            this.weather = results;
            var date = new Date();
            var now_utc = Date.UTC(
                date.getUTCFullYear(),
                date.getUTCMonth(),
                date.getUTCDate(),
                date.getUTCHours(),
                date.getUTCMinutes(),
                date.getUTCSeconds()
            );
            now_utc = now_utc - 7200000 // CONVERTION +2 GMT / CONVERTION +1 GMT HEURE d'HIVER
            now_utc = now_utc + (this.weather.timezone * 1000)   //CONVERSION MILLISEC 
            this.now_utcc = now_utc;
            this.ClockInit();
        },
        getLocalHours() {
            let hours = ((new Date(this.now_utcc)).getHours() > 9) ? (new Date(this.now_utcc)).getHours() : "0" + (new Date(this.now_utcc)).getHours();
            let minutes = ((new Date(this.now_utcc)).getMinutes() > 9) ? (new Date(this.now_utcc)).getMinutes() : "0" + (new Date(this.now_utcc)).getMinutes();
            let seconds = ((new Date(this.now_utcc)).getSeconds() > 9) ? (new Date(this.now_utcc)).getSeconds() : "0" + (new Date(this.now_utcc)).getSeconds();

            return hours + ":" + minutes + ":" + seconds;
        },
        ClockInit() {

            let date = new Date(this.now_utcc);
            //console.log(this.TownName+" - " + date);
            let seconds = date.getSeconds();
            let minutes = date.getMinutes();
            let hours = date.getHours();

            hours = (hours > 12) ? hours - 12 : hours;
            minutes = (minutes * 60) + seconds;
            seconds = (hours * 3600) + minutes;

            document.querySelector('.' + this.TownName + '-second-hand').setAttribute('transform', 'rotate(' + 360 * (seconds / 60) + ',192,192)');
            document.querySelector('.' + this.TownName + '-minute-hand').setAttribute('transform', 'rotate(' + 360 * (minutes / 3600) + ',192,192)');
            document.querySelector('.' + this.TownName + '-hour-hand').setAttribute('transform', 'rotate(' + 360 * (hours / 43200) + ',192,192)');
        },

    }
};
</script>
<style>
.ClockVueComponent {
    position: relative;
    color: #f5deb3;
    z-index: 1;
}

.ClockVueTownComponent {
    padding-bottom: 20px;
}

.ClockVueHourComponent {
    padding-top: 25px;
}
</style>