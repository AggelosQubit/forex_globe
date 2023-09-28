<template>
    <div  class="PairsGeneralComponent">
        <div  class="PairsComponent">
            <select @change="PairsInfos($event)" class="PairsSelectComponent form-control">
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
            <div class="PairsInfoComponent">
            <p></p>
        </div>
        </div>
    </div>
</template>
<style scoped>
    .PairsGeneralComponent{ 
        position: relative;
        text-wrap: nowrap;
		z-index: 1;
        height: 200px;
        display: flex;
        justify-content: space-around
        
	}
    .PairsComponent{
        width: 19%;
    }
    .PairsSelectComponent{
        text-align: justify;
        height: 60px;
    }
    .PairsSelectComponent :disabled{
        text-align: center;
    }
</style>
<script>
    export default{
        data(){
            return{
                pair:String,
                correspondance : [
                    { "primary":"EUR","Town":"Paris"},
                    { "primary":"USD","Town":"New York"},
                    { "primary":"GBP","Town":"London"},
                    { "primary":"CHF","Town":"Zurich"},
                    { "primary":"JPY","Town":"Tokyo"},
                    { "primary":"AUD","Town":"Sydney"},
                    { "primary":"NZD","Town":"Wellington, NZ"},
                    { "primary":"CAD","Town":"Toronto"},
                    { "primary":"TRY","Town":"Ankara"},
                    { "primary":"MXN","Town":"Mexico City"},
                    { "primary":"ZAR","Town":"Pretoria"},
                    { "primary":"HKD","Town":"Hong Kong, HK"},
                    { "primary":"SGD","Town":"Singapore"},
                    { "primary":"THB","Town":"Bangkok"},
                    { "primary":"SEK","Town":"Stockholm"},
                    { "primary":"DKK","Town":"Copenhague"},
                ]
            }
        },
        methods:{
            PairsInfos : ($event) => {
                console.log($event.target.value);
            }
        }
        
    }
</script>