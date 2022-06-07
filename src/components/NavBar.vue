<template>
  <nav class="navbar navbar-expand-lg navbar-light  shadow-lg bg-white rounded" >
    <div class="container">
        <a class="navbar-brand">Online Bus System</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
       
    <img :src="'/images/ako.jpg'" style="position:absolute; left:86%; top: 5px; border-radius: 50px;" >
     <h5 style="position:absolute; left:90%; top:15px; font-weight:100;">Kenn Secusana</h5> 
           
  
  <div class="btn-group" style="position:absolute; left: 83%; top: 10px;">
	  <button class="btn dropdown-toggle"  type="button" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
	
	  </button> 

	  <ul class="dropdown-menu dropdown-menu-left" >
		<li><a class="dropdown-item " href="/users">Profile</a></li>
		<li><a class="dropdown-item" href="#">Logout</a></li>
	  </ul>
   </div>

              
</ul>
</div>
</div>
    <img :src="'/images/path1281.png'" >
  </nav>


           <!-- Sidebar -->
           <div class="card col-md-2 shadow-lg p-3 mb-5 " style="background-color:#5bc0de; height: 558px; position:fixed; ">
           <nav id="sidebarMenu" class="collapse d-lg-block sidebar collapse" style="background-color:#5bc0de">
              <div class="position-sticky">
                <div class="list-group list-group-flush mx-3 mt-2">
                   <img :src="'/images/bitmapx.png'" style="height:15px; width:20px; position:absolute; top:-7px; left: 20px;" >
                  <router-link to="/" class="nav-link" style="left:15px; position:relative; margin-top: -20px; margin-bottom: -15px; color:white;">Dashboard</router-link>
                  <hr> 
                   <img :src="'/images/imagehey.png'" style="height:18px; width:20px; position:absolute; top: 35px; left: 23px;" >
                  <router-link to="/bookings" class="nav-link" style="left:15px; position:relative; margin-top: -15px; margin-bottom: -15px; color:white;">Bookings </router-link>
                  <hr>
                     <img :src="'/images/path39.png'" style="height:18px; width:18px; position:absolute; top: 78px; left: 23px;" >
                    <router-link to="/operators" class="nav-link" style="left:15px; position:relative; margin-top: -15px; margin-bottom: -15px; color:white;">Operators </router-link>
                  <hr>
                 </div>
                </div>
                 </nav>
              </div>

              <footer class="text-center text-lg-start col-md-2 shadow-lg mb-5" style="position:absolute; top:93.5%; width:83.4%; left:16.6%; background-color: #5bc0de;">
  <!-- Copyright -->
  <div class="text-end p-2">
    © 2022 Copyright:
    <a class="text-dark" href=""><i>onlinebusticketinginc.</i></a>
  </div>
  <!-- Copyright -->
</footer>




</template>



<script>
export default {

}
</script>

<style>

.first{
    position: absolute;
    left:80%;
    top: 10%;
}

.second{
    position: absolute;
    left:86%;
    top: 10%;
}

.third{
    position: absolute;
    left: 92%;
    top: 10%;
}

   img{
     position: absolute;
     height: 46px;
     width: 46px;
     top: 3px;
     left:24px;
   }




</style>