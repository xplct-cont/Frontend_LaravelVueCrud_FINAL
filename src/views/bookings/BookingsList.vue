<template>
  <div>
     
    
     
         <button class=" btn btn-sm" @click="toggleCreator" style= "background-color: #5bc0de;width:120px;position:absolute; left: 86.5%; top: 80px;;">{{creator.label}}</button>
         <div class="col-md-11  shadow-lg p-3 mb-5 bg-white rounded" style="position:relative; top:80px; left: 13%; ">
          <h1 class="text-center" style="color:DarkSlateGray; font-weight:normal; font-size:30px;">BOOKINGS</h1>
            <img :src="'/images/image1933.png'" style="position:absolute; top:8px;">
              <table class="table table-striped table-hover">
                      
                <thead class="text-center">
                    <tr>
                       
                        <th style="background-color:#5bc0de">Point Of Origin</th>
                        <th style="background-color:#5bc0de">Destination</th>
                        <th style="background-color:#5bc0de">Passenger Name</th>
                        <th style="background-color:#5bc0de">Age</th>
                        <th style="background-color:#5bc0de">Contact No</th>
                      
                       
                    </tr>
                </thead>
                <tbody class="text-center">
                    <tr v-for="booking in bookings" :key="booking.id" class="w3-hover-light-gray" style="cursor:pointer" @click="openBooking(booking.id)">
                     
                        <td>{{booking.point_of_origin}}</td>
                        <td>{{booking.destination}}</td>
                        <td>{{booking.passenger_name}}</td>
                        <td>{{booking.age}}</td>
                        <td>{{booking.contact_no}}</td>
                      
                      
                    </tr>
                </tbody>
            </table>
          </div>
      </div>
      <div v-if="creator.show">
      
           <div class="card   shadow-lg p-3  bg-white rounded" style=" height: 80% ;width: 64.5rem; left: 17.5%;top:20%; position:absolute;">
            <h1 class="text-center bg-info" style="color:DarkSlateGray; font-weight:normal; font-size:30px;  padding-top:10px; padding-bottom: 10px; border-radius: 5px;">CREATE BOOKINGS</h1>
             <img :src="'/images/image1933.png'" style="position:absolute; top:22px;">
           <hr>
               <div class="card-body">
               
                  <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px;">Point Of Origin &nbsp;</label> &nbsp;
                  <input type="text" v-model="booking.point_of_origin" style="width: 30%;">
                 </div>
                 

                  <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px;  position: absolute; left: 50%; top: 26.5%;">Destination &nbsp;</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                  &nbsp;&nbsp;
                  <input type="text" v-model="booking.destination" style="width: 30%; position: absolute; left: 64.5%; top: 26%;">
                 </div>

                 
                  <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px; position: absolute; left: 50%; top: 42.5%;">Passenger Name &nbsp;</label>
                  <input type="text" v-model="booking.passenger_name" style="width: 30%;  position: absolute; left: 64.5%; top: 42%;">
                 </div><br>
                 
                     <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px;">Age &nbsp;</label> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                  <input type="text" v-model="booking.age" style="width: 30%;">
                 </div>
                     <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px; position: absolute; left: 30px; top: 59.5%;">Contact No &nbsp;</label>
                  <input type="text" v-model="booking.contact_no" style="width: 28%;  position: absolute; left: 16.5%; top: 59%;">
                 </div>

                  <button class="btn btn-md btn-secondary border border-light" @click="submitBooking" style=" position:absolute; top:85%; left:40%;">Create Booking</button>
          
          </div>
          </div>
        </div>
    
 
</template>

<script>
export default {
    data() {
        return {
            booking: {
                id:null,
              
                point_of_origin:'',
                destination:'',
                passenger_name:'',
                age:'',
                contact_no: ''
                
            },
             creator: {
               show: false,
               label: "Create Booking"
           },

         

            bookings:[]
        }
    },

    methods: {

          toggleCreator(){
           if(this.creator.show){
               this.creator = {show:false, label:"Create Booking"}
           }else{
                this.creator = {show:true, label:"Cancel"}
           }
       },

        addBooking() {
           
        },
         
        getData(){
          fetch('http://192.168.1.4:8000/api/bookings')
          .then(response=>response.json())
          .then(data=>this.bookings = data)
          .catch(err=>console.log(err) )
        },

         openBooking(bookingId) {
            this.$router.push({
                name: 'view-booking',
                params: {
                    id: bookingId
                }
            })
        },
           
         submitBooking()  {
               fetch('http://192.168.1.4:8000/api/bookings', {
                   method: 'post',
                   headers: {
                       "Content-Type":"application/json"
                   },
                   
                   credentials: 'same-origin',
                   body: JSON.stringify(this.booking)
                  

               })
                    .then(res=>res.json())
                    .then(data=>{
                        this.bookings.unshift(data)
                        this.booking = {}
                        this.creator.show=false,
                        this.creator.label="Create Booking";
                    })
                    .catch(err=>console.log(err))

         },


    },

    mounted() {
      this.getData();
    },
}


</script>

<style>
</style>