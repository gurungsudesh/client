<template>
    <div id="menu">
      
        <nav class="navbar sticky-top navbar-expand navbar-light" style="font-weight:bold; background-color: white">
            <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
            
            <ul class="navbar-nav mr-auto mt-2 mt-lg-0"  >
            <li class="nav-item ">
            <router-link  class="nav-link" to="/about"><i class="fas fa-home"></i><label>Home</label></router-link>
            </li>
      <li class="nav-item" >
        <div  @click="showNotification">
        <router-link class="nav-link" to="#" ><i class="far fa-bell"></i><span class="badge">1</span><label style="margin-left:15px;">Notifications</label></router-link>
        </div>
        <div class="dpdownbody" id="notificationid" ref="notificationid">
            <h1 style="text-align:center; color:green; border-bottom: 1px solid grey; padding-bottom:30px;"><i class="fas fa-bell"></i></h1>
            <ul>
              <li >Notification 2</li>
              <li >Notification 2</li>
              <li >Notification 2</li>
            </ul>
            <div class="seemore">
              <router-link  class="nav-link" to="/notification"><b style="color:green"> See More</b></router-link>
            </div>            
        </div>
            
      </li>
      <li class="nav-item">
        <router-link class="nav-link" to="#"><i class="far fa-envelope"></i><label>Messages</label></router-link>
      </li>
    </ul> 
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button id="sbtn" class="btn btn-success" type="submit"><i class="fas fa-search" ></i></button>
    </form>
  <div id="dpdn" class="btn-group">
  <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
  </button>
  <div  class="dropdown-menu dropdown-menu-right">
    <router-link class="dropdown-item" to="/profile" >Profile</router-link>
    <router-link class="dropdown-item" to="/" >Settings</router-link>
    <button v-on:click="logout" ><router-link class="dropdown-item" to="/" >Log Out</router-link></button>
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
      },
      showNotification(){
        var vm = this;
        if(vm.$refs.notificationid.style.visibility == 'visible'){
          vm.$refs.notificationid.style.visibility = 'hidden';
          vm.$refs.notificationid.style.height = '0px';
          vm.$refs.notificationid.style.opacity = '0';
          
        }
          else
          {
            vm.$refs.notificationid.style.visibility = 'visible'
          vm.$refs.notificationid.style.opacity = '1';
          vm.$refs.notificationid.style.height = 'auto';
          }
        
        
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
#notificationid{
  transition: 0.3s;
  visibility: hidden;
  z-index: 1;
  position: absolute;
  height:0px;
  width:400px;
  background-color: white;
  border: 1px solid green;
  opacity: 0;
  border-radius: 20px;
  
  text-align:center;
}
.dpdownbody ul{
  list-style: none;
  margin: 0%;
  padding: 0%;
}
.dpdownbody li{
  border-bottom: 1px solid grey;
  padding: 10px;
}
.badge {
 
  padding: 4px 8px;
  border-radius: 50%;
  background: red;
  color: white;
  position: absolute;
  top: +10px;

  
}

.seemore{ 
  position: relative;
  width: 99.9%;
  bottom: 0%;
  padding: 5px;
  border-top: 1px solid green;
}
.seemore:hover{
  background-color: rgb(206, 255, 209); 
  cursor: pointer;
  border-radius: 0px 0px 20px 20px;

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

