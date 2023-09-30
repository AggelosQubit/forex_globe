<template>
    <div  class="PairsGeneralComponent">
        <div  class="PairsComponent">
            <div class="PairsSelectComponent">
                <select @change="PairsInfos($event)" class=" form-control">
                <option  disabled >Major Forex Pairs</option>
                <hr/>
                <option value="EUR_USD">EUR/USD – Euro/US dollar</option>
                <option value="USD_JPY">USD/JPY – US dollar/Japanese yen</option>
                <option value="GBP_USD">GBP/USD – British pound/US dollar</option>
                <option value="USD_CHF">USD/CHF – US dollar/Swiss franc</option>
                <option value="AUD_USD">AUD/USD – Australian dollar/US dollar</option>
                <option value="USD_CAD">USD/CAD – US dollar/Canadian dollar</option>
                <option value="NZD_USD">NZD/USD – New Zealand dollar/US dollar</option>   

                <option disabled value=""> Minor Forex Pairs</option>
                <hr/>

                <option value="EUR_GBP">EUR/GBP – Euro/British pound</option>
                <option value="EUR_CHF">EUR/CHF – Euro/Swiss franc</option>
                <option value="EUR_JPY">EUR/JPY – Euro/Japanese yen</option>
                <option value="GBP_JPY">GBP/JPY – British pound/Japanese yen</option>
                <option value="CHF_JPY">CHF/JPY – Swiss franc/Japanese yen</option>
                <option value="AUD_JPY">AUD/JPY – Australian dollar/Japanese yen</option>
                <option value="CAD_JPY">CAD/JPY – Canadian dollar/Japanese yen</option>
                <option value="NZD_JPY">NZD/JPY – New Zealand dollar/Japanese yen</option>
                <option value="AUD_NZD">AUD/NZD – Australian dollar/New Zealand dollar</option>
                <option value="AUD_CHF">AUD/CHF – Australian dollar/Swiss franc</option>
                <option value="GBP_CHF">GBP/CHF – British pound/Swiss franc</option>
                <option value="CAD_CHF">CAD/CHF – Canadian dollar/Swiss franc</option>

                <option disabled value="">Exotic Forex Pairs</option>
                <hr/>
                <option value="EUR_TRY">EUR/TRY – Euro/Turkish lira</option>
                <option value="USD_TRY">USD/TRY – US dollar/Turkish lira</option>
                <option value="USD_MXN">USD/MXN – US dollar/Mexican peso</option>
                <option value="USD_ZAR">USD/ZAR – US dollar/South African rand</option>
                <option value="USD_HKD">USD/HKD – US dollar/Hong Kong dollar</option>
                <option value="USD_SGD">USD/SGD – US dollar/Singapore dollar</option>
                <option value="USD_THB">USD/THB – US dollar/Thai baht</option>
                <option value="USD_SEK">USD/SEK – US dollar/Swedish krona</option>
                <option value="USD_DKK">USD/DKK – US dollar/Danish krone</option>
            </select>
            </div>
        </div>
        <div v-if="filled" class="PairsInfoComponent">
            <div class="TownCardElement">
                <ClockVue :key="componentKey" :TownName="TownPrimary"/>
            </div>
            <div class="TownCardElement">
                <ClockVue :key="componentKey" :TownName="TownSecondary"/>
            </div>
        </div>
    </div>
</template>
<style scoped>
    .PairsGeneralComponent{ 
        position: relative;
        text-wrap: nowrap;
		z-index: 1;
        display: block;
	}
    .PairsComponent{
        display: flex;
        justify-content: space-around;
    }
    .PairsSelectComponent{
        width: 19%;
        height: 60px;
    }
    .PairsSelectComponent :disabled{
        text-align: center;
    }

    .PairsInfoComponent{
        display: flex;
        flex-direction: row;
        justify-content: space-around
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
<script>
    import ClockVue from './ClockVue.vue';
    import { ref } from 'vue';

    export default{
        components :{
            ClockVue
        },
        data(){
            return{
                componentKey: ref(0),
                pair:String,
                correspondance :Map,
                filled:false,
                TownPrimary:String,
                TownSecondary:String
            }
        },
        created(){
            this.correspondance = new Map() 
            this.correspondance.set("EUR","Paris");
            this.correspondance.set("USD","New York");
            this.correspondance.set("GBP","London");
            this.correspondance.set("CHF","Zurich");
            this.correspondance.set("JPY","Tokyo");
            this.correspondance.set("AUD","Sydney");
            this.correspondance.set("NZD","Wellington, NZ");
            this.correspondance.set("CAD","Toronto");
            this.correspondance.set("TRY","Ankara");
            this.correspondance.set("MXN","Mexico City");
            this.correspondance.set("ZAR","Pretoria");
            this.correspondance.set("HKD","Hong Kong, HK");
            this.correspondance.set("SGD","Singapore");
            this.correspondance.set("THB","Bangkok");
            this.correspondance.set("SEK","Stockholm");
            this.correspondance.set("DKK","Copenhague");
            console.log("IN CREATED");
            console.log( this.correspondance);
        },  
        methods:{
            PairsInfos : function ($event){
                let pairCurrency = ($event.target.value).split("_");
                console.log("ComponentKey : " + this.componentKey);
                this.filled=false;
                
                this.TownPrimary    =this.correspondance.get(pairCurrency[0]);
                this.TownSecondary  =this.correspondance.get(pairCurrency[1]);
                this.filled=true;
                this.forceRerender();
            },
            forceRerender: function() {
                this.componentKey += 1;
            }
        }
        
    }
</script>