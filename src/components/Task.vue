<template>
  <div class="container-fluid">
      <h1 style="text-align:center">Remoteplatz  Task</h1>
            <div class="col-md-12">
                <div class="card">
                    <div class="card-header">
                        Fetching Data From An API Using Vuejs
                    </div>
                    <div class="card-body">
                        <div class="row">
                            <div class="col-md-6 text-center infos">
                                <label for="purchasePrice" >Purchase price</label>
                                <input type="text" class="form-control inpFields firstCol" style="width: 345px" id="purchasePrice" :value="price">
                                <span style="font-weight: bold;left: 37%;display: inline;top: -43px;position: relative;font-size: 16px;">{{currency}}</span>
                                <select name="" id="dropdownBar">
                                    <option value=""></option>
                                    <option :value="currency">{{currency}}</option>
                                </select>
                            </div>
                            <div class="col-md-6 text-center infos">
                                        <label for="plotSize" class="secCol" style="padding-right: 41px">Plot size</label>
                                        <input type="text" class="form-control inpFields " id="plotSize" :value="plotSize">
                                        <span style="font-weight: bold;right: 126px;display: inline;top: -43px;position: relative;font-size: 16px;border-left: 1px solid lightgrey;padding: 0 15px;">m<sup>2</sup></span>
                            </div>
                            <div class="col-md-6 text-center infos">
                                    <label for="yearOfConst" style="position: relative; left: 22px">Year of construction</label>
                                    <input type="text" class="form-control inpFields firstCol" id="yearOfConst" :value="yearOfConstruct">
                            </div>
                            <div class="col-md-6 text-center infos">
                                    <label for="netRent" class="secCol" style="padding-left: 33px;">Net rent total (p.a)</label>
                                    <input type="text" class="form-control inpFields" id="netRent" style="color: #b5b0b0" :value="netRentTotal">
                                    <span style="font-weight: bold;right: 150px;display: inline;top: -43px;position: relative;font-size: 16px;border-left: 1px solid lightgrey;padding: 0 15px;">{{currency}} / p.a.</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
    </div>
</template>

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
</script>

<style>

    .card {
        font-family: cursive;
        
    }

    .row {
        background: #d3d3d36e;
        padding: 0;
        border-radius: 10px;
        padding-top: 45px;
    }

   .inpFields {
       width: 200px;
       height: 60px;
       box-shadow: 5px 10px 5px lightgrey
   }

   .firstCol {
        position: relative;
        left: 41%;
   }

   .infos {
       margin-bottom: 30px;
   }

   .secCol {
        position: relative;
        right: 41%;
   }

   #dropdownBar {
        height: 60px;
        text-align: center;
        border: 1px solid lightgray;
        padding: 0;
        position: absolute;
        top: in;
        right: 30px;
        width: 43px;
        bottom: 24px;
        border-radius: 0 5px 5px 0;
   }
</style>