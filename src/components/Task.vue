<template>
  <div class="container">
      <h3 style="text-align:center">Remoteplatz  Task</h3>
        <div class="row">
            <div class="col s12 m12 ">
                <div class="card">
                    <form class="col s12" id="myForm">
                        <div class="row">
                            <div class="input-field col s5 m5">
                                <input class="inputFields" :placeholder="price" id="first_name" type="text" :value="price" style="width: 100% !important">
                                <label class="labelsI" for="first_name">Purchase price</label>
                                <span  class="currencyF">{{currency}}</span>
                            </div>
                            <div class="input-field col s1 m1 mySelect" style="border-bottom: none !important;">
                                <select class="" style="border-bottom: none !important;">
                                    <option value="" selected></option>
                                    <option value="1">EUR</option>
                                    <option value="2">$</option>
                                </select>
                            </div>
                            <div class="input-field col s6">
                                <input class="inputFields" :placeholder="plotSize" id="last_name" type="text" :value="plotSize">
                                <label class="labelsI" for="last_name">Plot size</label>
                                <span  class="measureP">m<sup>2</sup></span>
                            </div>
                        </div>
                        <div class="row">
                            <div class="input-field col s6">
                                <input class="inputFields" :placeholder="yearOfConstruct" id="first_name" type="text" :value="yearOfConstruct">
                                <label class="labelsI" for="first_name">Year of construction</label>
                            </div>
                            <div class="input-field col s6">
                                <input class="inputFields" :placeholder="netRentTotal" id="last_name" style="    color: #8a8a8a;" type="text" :value="netRentTotal">
                                <label class="labelsI" for="last_name">Net rent total (p.a)</label>
                                <span  class="currencyP">{{currency}} / p.a.</span>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>
<script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script>
const axios = require('axios');

export default {
    name: "Task",
    data() {
        return {
            price: '',
            yearOfConstruct: '',
            plotSize: '',
            netRentTotal: '',
            currency: ''
        }
    },
    mounted: function() {
        const url = "https://server.offmade.io/code-challenge";
        axios.get(url).then((response ) => {
            const { price, netRentTotal, plotSize, yearOfConstruction, currency} = response.data;
            this.price = price;
            this.currency = currency;
            this.yearOfConstruct = yearOfConstruction;
            this.plotSize = plotSize;
            this.netRentTotal = netRentTotal;
        });
    },
}

  // Or with jQuery

  $(document).ready(function(){
    $('select').formSelect();
  });
</script>

<style scoped>
    #myForm{
        background: rgba(243, 243, 243, 0.54) !important;
        padding: 80px !important;
        border-radius: 10px;
    }

   .inputFields {
        background: #fff !important;
        padding-left: 25px !important;
        width: 55% !important;
        height: 80px !important;
        font-size: 25px !important;
        border-radius: 5px !important;
        border: none !important;
        font-weight: 500 !important;
   }

   .mySelect {
        background: #fff !important;
        height: 80px !important;
        border-radius: 5px !important;
        position: relative !important;
        padding: 18px !important;
        right: 55px !important;
        border-bottom: none !important;
        border-left: 1px solid black !important;
        border-width: 0px !important;
   }

   .labelsI {
        font-weight: bold;
        top: -20px;
        font-size: 18px;
   }

    .currencyF,
    .currencyP,
    .measureP{
        position: relative;
        bottom: 63px;
        font-weight: bold;
        font-size: 18px;
        overflow: visible;
        z-index: 55555555555;
        color: rgb(179, 174, 174);
        font-style: italic;

    }  

   .currencyF {
        left: 75%;
        border-right: 1px solid lightgray;
        padding-right: 10px;
   }
   .currencyP{
        right: 100px;
        bottom: 3px;
        border-left: 1px solid lightgray;
        padding-left: 10px;
   }
   
   .measureP {
        right: 45px;
        bottom: 8px;
        border-left: 1px solid lightgray;
        padding-left: 10px;
   }
</style>