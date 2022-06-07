<template>
    <h1 style="position:absolute; left:20.5%;">Operator Information</h1>
   
<div class="card shadow-lg p-3 mb-5 bg-white rounded" style="width: 60rem; height:13rem; position:relative;
     left:16%; top: 50px;">  
          <div class="card-header">
                <button class="btn btn-sm bg-danger" style="color:white; position:relative; left: 93.5%; top: 140px;" @click="deleteOperator"> Delete</button>
                    <button class=" btn btn-sm bg-warning" @click="toggleEditor" style= "position:relative; left: 82.7%;">{{editor.label}}</button>
                     <img :src="'/images/image17.png'" style="position:absolute; top:17px;">
                      <table class="table table-hover text-center" style="margin-top:20px;">
                            <tr>

                     
                        <th style="background-color:#5bc0de">Operator Name</th>
                        <th style="background-color:#5bc0de">Address</th>
                        <th style="background-color:#5bc0de">Contact No</th>
                      
                            </tr>
                          
                            <tr>
                  
                        <td>{{operator.operator_name}}</td>
                        <td>{{operator.address}}</td>
                        <td>{{operator.contact_no}}</td>
                     
                            </tr>             
                            
                    </table>
             </div>
            <div>
      
           
             <div v-if="editor.show">
           <div class="card   shadow-lg p-3  bg-white rounded" style=" height: 31.5rem ;width: 60rem; left: 0%;top:0%; position:absolute;">
            <h1 class="text-center bg-info" style="color:DarkSlateGray; font-weight:normal; font-size:30px;  padding-top:10px; padding-bottom: 10px; border-radius: 5px;">EDIT OPERATOR</h1>
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
                     
                         <button class=" btn btn-sm bg-warning" @click="toggleEditor" style= "position:absolute; left: 88%; top: 30px;">{{editor.label}}</button>
                     <button class="btn btn-sm btn-success" style="color:white; position:relative; left: 44.5%; top: 200px;" @click="saveOperator">Update</button>
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
           operator: {},
           editor: {
               show: false,
               label: "Edit Operator"
           }
       }
   },

   methods: {

       toggleEditor(){
           if(this.editor.show){
               this.editor = {show:false, label:"Edit Operator"}
           }else{
                this.editor = {show:true, label:"Cancel"}
           }
       },
       saveOperator(){
                fetch('http://192.168.1.4:8000/api/operators/' + this.operator.id,{
                    method: 'put',
                    headers: {
                        'Content-Type' : "application/json"
                    },
                    credentials: 'same-origin',
                    body: JSON.stringify(this.operator)
                 })
                 .then(res=>res.json())
                 .then(data=>{
                       this.editor.show=false;
                       this.editor.label="Edit Operator";

                 })
                 .catch(err => console.log(err))
       },
          deleteOperator(){
                 fetch('http://192.168.1.4:8000/api/operators/' + this.operator.id,{
                       method:'delete'
                 })
                 .then(res=>res.json())
                 .then(data=>{
                     alert("Operator has been deleted")
                     this.$router.push({
                        name: 'all-operators'
                     })
                    
                 })
                 .catch(err=>console.log(err))
         }
   },

   mounted(){
       fetch('http://192.168.1.4:8000/api/operators/' + this.id)
       .then(res => res.json())
       .then(data => this.operator = data)
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