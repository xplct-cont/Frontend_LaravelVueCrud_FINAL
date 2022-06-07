<template>
  
  <div class="card shadow-lg p-3 mb-5" style="width: 45rem; height: 20rem;">
<div class="card-body">
<div class="container">
    <div class="row">
        <div class="col-md-10 col-md-offset-1">
            <img src="/images/ako.jpg" style="width: 150px; height:150px; border-radius: 50%; float:left; margin-right:25px; margin-top: 20px;">
             <h2 style="position:absolute; left: 27%;">Administrator's Profile</h2>
             <form enctype="multipart/form-data" action="#" method="POST">   
                <label  style="position:absolute; left: 27%; top: 25%;">Update Profile Image</label><br>
                <input type="file" name="avatar"  style="position:absolute; left: 27%; top: 35%;">
                <input type="hidden" name="_token" value="{{ csrf_token() }}"><br><br>
                <div class="btv">
                <input type="submit" class=" btn btn-sm btn-info"  style="position:absolute;  left: 55%; top: 140px;">
            </div>
            </form>
        </div>
      
        </div>
    </div>
 </div>
</div>

</template>

<script>
export default {

}
</script>

<style scoped >


    .card{
        position: fixed;
        top: 20%;
        left: 31%;
        background-color:#f7f7f7;
    }
     
    .container{
        position: inherit;
        top: 30%;
        left: 40%;
    }
    .btv {
        position: relative;
        left: 50%;
    }


</style>