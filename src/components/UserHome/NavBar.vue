<template>
    <div id="menu">
      
        <nav class="navbar sticky-top navbar-expand navbar-light" style="font-weight:bold; background-color: white">
            <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
            
            <ul class="navbar-nav mr-auto mt-2 mt-lg-0"  >
            <li class="nav-item ">
            <a class="nav-link" href="#"><i class="fas fa-home"></i><label>Home</label></a>
            </li>
      <li class="nav-item">
        <a class="nav-link" href="#"><i class="far fa-bell"></i><label>Notifications</label></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#"><i class="far fa-envelope"></i><label>Messages</label></a>
      </li>
    </ul> 
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button id="sbtn" class="btn btn-success" type="submit"><i class="fas fa-search" ></i><label>Search</label></button>
    </form>
  <div id="dpdn" class="btn-group">
  <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
  </button>
  <div  class="dropdown-menu dropdown-menu-right">
    <router-link class="dropdown-item" to="/profile" >Profile</router-link>
    <router-link class="dropdown-item" to="/" >Settings</router-link>
    <router-link class="dropdown-item" to="/" v-on:click="logout">Log Out</router-link>
</div>
  </div>
  </div>
</nav> 
       
       
    </div>
</template>

<script>
export default {
    name: "NavBar",
    methods:{
      logout(){
        localStorage.removeItem('usertoken')
      }
    }
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
#sbtn{
  display: inline-flex;
}
label{
  padding-left: 10px;
}

a{  
    font-size: 17px;
   font-family: Arial, Helvetica, sans-serif;
    margin-left: 10px;
    border-radius: 10px;
    color:black;
    text-decoration:none;
}
@media only screen and (max-width: 900px) {
  nav li:nth-child(1) label {
    display: none;
  }
  nav li:nth-child(2) label {
    display: none;
  }
  nav li:nth-child(3) label {
    display: none;
  }
  nav li i{
    font-size: 20px;
  }
  nav form label{
    display: none;
  }
  nav form input[type=search]{
    width: 70% ;
   
  }
  nav form{
    position: flex;
    
  }
  #dpdn{
    position: absolute;
    right: 0px;
  }
  #dpdn button{
    transform: scale(0.8)
  }
}

</style>

