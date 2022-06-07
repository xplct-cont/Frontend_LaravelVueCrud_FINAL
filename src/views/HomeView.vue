<script setup>
</script>
<template>
       
            <img src="/images/background.png" >

           <div class="ss">
            <div class="card shadow-lg p-3 mb-5 bg-white rounded" style="width: 16rem; height:20rem;">
              <img class="card-img-top" style="height:170px;  width: 16rem; left: -1px; position:absolute; top:0px;" src="/images/bus.jpg">
                 <div class="card-body">
                     <h5 class="card-title" style="top:60%; position:relative; font-size:15px; font-weight:bold;">Save $100 on Luxury Bus Rental</h5>
                       <p class="card-text"  style="top:58%; position:relative; font-size:13px;">Looking for a cheap weeekly Bus fare that wont't leave your wallet empty?</p>
                        <p class="card-text"  style="top:55%; position:relative; font-size:13px; font-weight:bold;">Price:$<del style="font-weight:normal;">120</del> 100</p>
              </div>
           </div>
        </div>

         <div class="sd">
            <div class="card shadow-lg p-3 mb-5 bg-white rounded" style="width: 16rem; height:20rem;">
              <img class="card-img-top" style="height:170px;  width: 16rem; left: -1px; position:absolute; top:0px;" src="/images/eating.jpg">
                 <div class="card-body">
                     <h5 class="card-title" style="top:60%; position:relative; font-size:15px; font-weight:bold;">Season Bus Lunch Discount</h5>
                       <p class="card-text"  style="top:58%; position:relative; font-size:13px;">Promotional Deals starting from 100$ per day</p>
                        <p class="card-text"  style="top:63%; position:relative; font-size:13px; font-weight:bold;">Price:$<del style="font-weight:normal;">150</del> 100</p>
              </div>
           </div>
        </div>

        <div class="sf">
            <div class="card shadow-lg p-3 mb-5 bg-white rounded" style="width: 16rem; height:20rem;">
              <img class="card-img-top" style="height:170px; width: 16rem; left: -1px; position:absolute; top:0px;" src="/images/lpbus.jpg">
                 <div class="card-body">
                     <h5 class="card-title" style="top:60%; position:relative; font-size:15px; font-weight:bold;">Low Prices on Rental Bus Everyday</h5>
                       <p class="card-text"  style="top:58%; position:relative; font-size:13px;">Bus for discounted rates and weekly specials</p>
                        <p class="card-text"  style="top:63%; position:relative; font-size:13px; font-weight:bold;">Price:$<del style="font-weight:normal;">350</del> 310</p>
              </div>
           </div>
        </div>

       

</template>

<script>
export default {
data () {
    return {
       
    }
},

methods: {
     getData(){
          fetch('http://localhost:8000/api/bookings')
          .then(response=>response.json())
          .then(data=>this.bookings = data)
          .catch(err=>console.log(err) )
        },
}

}



</script>


<style scoped>

img{
    position: absolute;
    width: 83%;
    height:91%;
    top:9%;
    left:17%;
}

.ss{
    position: absolute;
    top: 17%;
    left: 21%;
}


.sd{
    position: absolute;
    top: 17%;
    left:48%;
}

.sf{
    position: absolute;
    top: 17%;
    left:75%;
}


</style>
