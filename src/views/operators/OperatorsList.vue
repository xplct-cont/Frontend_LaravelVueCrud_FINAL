<template>
  <div>
     
         <button class=" btn btn-sm" @click="toggleCreator" style= "background-color: #5bc0de;width:120px;position:absolute; left: 86.5%; top: 80px;;">{{creator.label}}</button>
         <div class="col-md-11  shadow-lg p-3 mb-5 bg-white rounded" style="position:relative; top:80px; left: 13%; ">
          <h1 class="text-center" style="color:DarkSlateGray; font-weight:normal; font-size:30px;">OPERATORS</h1>
            <img :src="'/images/image17.png'" style="position:absolute; top:8px;">
              <table class="table table-striped table-hover">
                      
                <thead class="text-center">
                    <tr>
                      
                        <th style="background-color:#5bc0de">Operator Name</th>
                        <th style="background-color:#5bc0de">Address</th>
                        <th style="background-color:#5bc0de">Contact No</th>
                       
                      
                       
                    </tr>
                </thead>
                <tbody class="text-center">
                    <tr v-for="operator in operators" :key="operator.id" class="w3-hover-light-gray" style="cursor:pointer" @click="openOperator(operator.id)">
                       
                        <td>{{operator.operator_name}}</td>
                        <td>{{operator.address}}</td>
                        <td>{{operator.contact_no}}</td>
                     
                      
                      
                    </tr>
                </tbody>
            </table>
          </div>
      </div>
      <div v-if="creator.show">
      
           <div class="card   shadow-lg p-3  bg-white rounded" style=" height: 80% ;width: 64.5rem; left: 17.5%;top:20%; position:absolute;">
            <h1 class="text-center bg-info" style="color:DarkSlateGray; font-weight:normal; font-size:30px;  padding-top:10px; padding-bottom: 10px; border-radius: 5px;">Add Operators</h1>
             <img :src="'/images/image17.png'" style="position:absolute; top:22px;">
           <hr>
               <div class="card-body">
           
                 <div>
                  <label for="title" style=" padding-left:10px; border-radius: 2px; position: absolute; left: 25%; top: 26.5%;">Operator Name &nbsp;</label>&nbsp;
                  <input type="text" v-model="operator.operator_name" style="width: 30%;  position: absolute; left: 40.5%; top: 26%;">
                 </div>

                  <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px;  position: absolute; left: 25%; top: 40.5%;">Address &nbsp;</label> &nbsp;
                  <input type="text" v-model="operator.address" style="width: 30%;  position: absolute; left: 40.5%; top: 40%;">
                 </div>
                 
                     <div>
                  <label for="title"  style=" padding-left:10px; border-radius: 2px; position: absolute; left: 25%; top: 55.5%;">Contact No &nbsp;</label> &nbsp;
                  <input type="text" v-model="operator.contact_no" style="width: 30%; position: absolute; left: 40.5%; top: 55%;">
                 </div>

               

                  <button class="btn btn-md btn-secondary border border-light" @click="submitOperator" style=" position:absolute; top:85%; left:40%;">Create Operator</button>
          
          </div>
          </div>
        </div>
    
 
</template>

<script>
export default {
    data() {
        return {
            operator: {
                id:null,
                operator_name:'',
                address:'',
                contact_no:'',
                
                
                
            },
             creator: {
               show: false,
               label: "Add Operator"
           },

           
            

            operators:[]
        }
    },
    methods: {

          toggleCreator(){
           if(this.creator.show){
               this.creator = {show:false, label:"Add Operator"}
           }else{
                this.creator = {show:true, label:"Cancel"}
           }
       },

        addBooking() {
           
        },
         
        getData(){
          fetch('http://192.168.1.2:8000/api/operators')
          .then(response=>response.json())
          .then(data=>this.operators = data)
          .catch(err=>console.log(err) )
        },

         openOperator(operatorId) {
            this.$router.push({
                name: 'view-operator',
                params: {
                    id: operatorId
                }
            })
        },
           
         submitOperator()  {
               fetch('http://192.168.1.2:8000/api/operators', {
                   method: 'post',
                   headers: {
                       "Content-Type":"application/json"
                   },
                   
                   credentials: 'same-origin',
                   body: JSON.stringify(this.operator)
                  

               })
                    .then(res=>res.json())
                    .then(data=>{
                        this.operators.unshift(data)
                        this.operator = {}
                        this.creator.show=false,
                        this.creator.label="Add Operator";
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