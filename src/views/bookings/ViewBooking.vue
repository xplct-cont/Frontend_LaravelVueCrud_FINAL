<template>
    <h1 style="position:absolute; left:20.5%;">Booked Information</h1>
   
<div class="card shadow-lg p-3 mb-5 bg-white rounded" style="width: 60rem; height:13rem; position:relative;
     left:16%; top: 50px;">  
          <div class="card-header">
                <button class="btn btn-sm bg-danger" style="color:white; position:relative; left: 93.5%; top: 140px;" @click="deleteBooking"> Delete</button>
                    <button class=" btn btn-sm bg-warning" @click="toggleEditor" style= "position:relative; left: 82.7%;">{{editor.label}}</button>
                       <img :src="'/images/image1933.png'" style="position:absolute; top:22px;">
                      <table class="table table-hover text-center" style="margin-top:20px;">
                            <tr>

                     
                        <th style="background-color:#5bc0de">Point Of Origin</th>
                        <th style="background-color:#5bc0de">Destination</th>
                        <th style="background-color:#5bc0de">Passenger Name</th>
                        <th style="background-color:#5bc0de">Age</th>
                        <th style="background-color:#5bc0de">Contact No</th>
                      
                            </tr>
                          
                            <tr>
                   
                        <td>{{booking.point_of_origin}}</td>
                        <td>{{booking.destination}}</td>
                        <td>{{booking.passenger_name}}</td>
                        <td>{{booking.age}}</td>
                        <td>{{booking.contact_no}}</td>
                            </tr>             
                            
                    </table>
             </div>
            <div>
      
           
             <div v-if="editor.show">
           <div class="card   shadow-lg p-3  bg-white rounded" style=" height: 31.5rem ;width: 60rem; left: 0%;top:0%; position:absolute;">
            <h1 class="text-center bg-info" style="color:DarkSlateGray; font-weight:normal; font-size:30px;  padding-top:10px; padding-bottom: 10px; border-radius: 5px;">EDIT BOOKING</h1>
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
                  <input type="text" v-model="booking.contact_no" style="width: 28%;  position: absolute; left: 17.5%; top: 59%;">
                 </div>
                     
                         <button class=" btn btn-sm bg-warning" @click="toggleEditor" style= "position:absolute; left: 88%; top: 30px;">{{editor.label}}</button>
                     <button class="btn btn-sm btn-success" style="color:white; position:relative; left: 44.5%; top: 150px;" @click="saveBooking">Update</button>
                   </div>
                 </div>
          </div>
        </div>
     </div>

</template>

<script>
export default{
    props:['id'],
  
   data(){
       return{
           booking: {},
           editor: {
               show: false,
               label: "Edit Booking"
           }
       }
   },

   methods: {

       toggleEditor(){
           if(this.editor.show){
               this.editor = {show:false, label:"Edit Booking"}
           }else{
                this.editor = {show:true, label:"Cancel"}
           }
       },
       saveBooking(){
                fetch('http://192.168.1.4:8000/api/bookings/' + this.booking.id,{
                    method: 'put',
                    headers: {
                        'Content-Type' : "application/json"
                    },
                    credentials: 'same-origin',
                    body: JSON.stringify(this.booking)
                 })
                 .then(res=>res.json())
                 .then(data=>{
                       this.editor.show=false;
                       this.editor.label="Edit Booking";

                 })
                 .catch(err => console.log(err))
       },
          deleteBooking(){
                 fetch('http://192.168.1.4:8000/api/bookings/' + this.booking.id,{
                       method:'delete'
                 })
                 .then(res=>res.json())
                 .then(data=>{
                     alert("Booking has been deleted")
                     this.$router.push({
                        name: 'all-bookings'
                     })
                    
                 })
                 .catch(err=>console.log(err))
         }
   },

   mounted(){
       fetch('http://192.168.1.4:8000/api/bookings/' + this.id)
       .then(res => res.json())
       .then(data => this.booking = data)
       .then(err => console.log(err))
   }

}

</script>

<style scoped>
 h1{
     color:DarkSlateGray;
     font-weight:normal;
     font-size:35px;
 }

 td{
     color:DarkSlateGray;
 }

</style>