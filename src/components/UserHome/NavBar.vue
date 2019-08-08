<template>
    <div id="menu">
      
        <nav class="navbar navbar-expand-lg navbar-light" style="font-weight:bold; background-color: white">
            <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
            
            <ul class="navbar-nav mr-auto mt-2 mt-lg-0"  >
            <li class="nav-item ">
            <a class="nav-link" href="#"><i class="fas fa-home"></i>.Home</a>
            </li>
      <li class="nav-item">
        <a class="nav-link" href="#"><i class="far fa-bell"></i>.Notifications</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#"><i class="far fa-envelope"></i>.Messages</a>
      </li>
    </ul> 
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-success" type="submit">Search  </button>
    </form>
  <div id="dpdn" class="btn-group">
  <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
  </button>
  <div  class="dropdown-menu dropdown-menu-right">
    <router-link class="dropdown-item" to="/" >Profile</router-link>
    <router-link class="dropdown-item" to="/" >Settings</router-link>
    <router-link class="dropdown-item" to="/" >Log Out</router-link>
</div>
  </div>
  </div>
</nav> 
        <!--<div id="menu">
                <a href="home.html">Home</a>
                <a href="notification.html">Notifications</a>
                <a href="">Messages</a>
            </div>
            <div class ="home-search">
                    
                <input type="search" value="Search ">
                <input type="submit" value="Search">
                <img src="bullet.jpg" id="otherprofileicon" >
                
            </div>-->
       
    </div>
</template>

<script>
export default {
    name: "NavBar"
}
</script>
<style scoped>
#dpdn{
  margin-left: 10px;
}
 #dpdn a{
   font-size: 14px;
    margin-left: 0px;
    
}
#dpdn a:active{
  background-color: green;
    
}
a{  
    font-size: 17px;
   font-family: Arial, Helvetica, sans-serif;
    margin-left: 10px;
    border-radius: 10px;
    color:black;
    text-decoration:none;
}

</style>

<!--<style>

 
.home-search{
    position: absolute;
    top:0px;
    right: 0px;
    padding-top:10px;
    }
#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   vertical-align:top  ;
   border: 3px solid darkgrey;
  
  
}

input[type="submit"] {
    background-color: lightgray;
    font-size: 15px;
    font-weight: bold;
    padding: 5px;
    padding-left: 15px;
    padding-right: 15px ;
    margin-left: 5px;
    margin-right: 5px;
    border-radius: 10px;
    color:rgb(56, 0, 0);
    border: none;
    vertical-align:middle;
    
}
input[type="submit"]:hover{
background-color: gray;
}
</style>
-->