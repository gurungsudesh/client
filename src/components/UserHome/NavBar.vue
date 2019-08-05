<template>
    <div id="menu">
        <nav class="navbar navbar-expand-lg navbar-dark" style="background-color: #5bd658">
  <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
    <ul class="navbar-nav mr-auto mt-2 mt-lg-0"  >
      <li class="nav-item active">
      <a class="nav-link" href="#">Home</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Notifications</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Messages</a>
      </li>
    </ul>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-success" type="submit">Search</button>
      
    </form>
    <router-link style="text-decoration:none; color:white; padding:5px;" to="/">Log Out</router-link>
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
a{  
    font-size: 17px;
   font-family: Arial, Helvetica, sans-serif;
    margin-left: 10px;
    border-radius: 10px;
}
 a:hover{
    background-color: rgb(30, 146, 30);
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