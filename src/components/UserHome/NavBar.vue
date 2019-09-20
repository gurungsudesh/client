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
        <router-link class="nav-link" to="#" ><i class="far fa-bell"></i><span id="badge1" ref="badge1" class="badge" >{{notifications.length}}</span><label style="margin-left:5px;" >Notifications</label></router-link>
        </div>
        <div class="dpdownbody" id="notificationid" ref="notificationid">
            <h1 style="text-align:center;  color:green;  padding-bottom:10px;"><i class="fas fa-bell"></i></h1>
            <ul style="text-align:left; border-top: 1px solid grey">
              <div v-for="(item,index) in notifications.slice(0, 7) " :key="index" style="padding-right:1px;">
                <div v-if="(checkname(item.sender) && (item.type==1 || item.type==2))">
                  <!--route rakha yaha post-->
                  
                  <router-link :to="{name:'postpage', params: {postID: item.postId }}"><li><b style="color:green; font-size:17px;">{{item.sender}}</b> {{`${switching(item.type)}`}}</li></router-link>
                </div>
                <div v-if="(checkname(item.sender) && (item.type==3 || item.type==4))">
                  <!--route rakha yaha follow-->
                  <router-link :to="{name:'otherprofile', params: {name: item.sender }}"><li><b style="color:green; font-size:17px;">{{item.sender}}</b> {{`${switching(item.type)}`}}</li></router-link>
                </div>
              </div>
            </ul>
            <div class="seemore">
              <router-link  class="nav-link" to="/notification"><b style="color:green"> See More</b></router-link>
            </div>            
        </div>
            
      </li>
      <li class="nav-item">
        <router-link class="nav-link" to="/messages"><i class="far fa-envelope"></i><label>Messages</label></router-link>
      </li>
    </ul> 
    <form class="form-inline my-2 my-lg-0" >
      <input class="form-control mr-sm-2" type="search" @input="search" placeholder="Search for the username" aria-label="Search" v-model="searchContent">
      <button id="sbtn" class="btn btn-success" @click="showNotification1(false)"><i class="fas fa-search" ></i></button>
      <div class="dpdownbody1" id="notificationid1" ref="notificationid1">
            <span style="font-size:30px; color:green;" >Search result</span>
            <ul style="text-align:left; border-top: 1px solid grey">
              <label style="margin-top:20px; margin-bottom:20px;" v-if="(user.length==0)" >Nothing to show</label>
              <div v-for="(item,index) in user" :key="index">
                <router-link :to="{name:'otherprofile', params: {name: item.name }}"><li ><img src="../../../images/ProfilePic.jpg"  id="posticon"> <span style=" font-size:17px; ">
                  {{item.name}}</span> </li> </router-link>
              </div>
            </ul>
                    
        </div>
    </form>
      <div id="dpdn" class="btn-group">
        <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        </button>
      <div  class="dropdown-menu dropdown-menu-right">
        <router-link class="dropdown-item" to="/profile" >Profile</router-link>
        <router-link class="dropdown-item" to="/account" >Settings</router-link>
        <div v-on:click="logout" ><router-link class="dropdown-item" to="/" >Log Out</router-link></div>
    </div>
  </div>
  </div>
</nav> 
       
       
    </div>
</template>

<script>
import jwtDecode from 'jwt-decode'
import axios from 'axios'
export default {
    name: "NavBar",
    data(){
      const token = localStorage.usertoken
      const decode = jwtDecode(token)
      return{
        name: decode.name,
        notifications: [],
        searchContent: '',
        user: []
      }
    },
    created(){
      axios.get(`http://localhost:5000/users/notifications/${this.name}`)
          .then(res=>{
            if(res.data.success){
              this.notifications = res.data.docs;
            }
          })
          .catch(err => alert(err));
    },
    updated(){
      var vm=this;
      if(this.notifications.length==0){
        vm.$refs.badge1.style.display='none';
      }
      
    },
    methods:{
      checkname(value){
        if(value==this.name){
          return false;
        }
        else{
          return true;
        }
        
      },
      switching(value){
        switch(value){
         case "1":
            return("liked your post.");

          case "2":
             return("commented on your post.");
            
          case "3":
             return("has followed you.");
            
            case "4":
             return("has unfollowed you.");
            
        }
      },
      search(){
        axios.post(`http://localhost:5000/users/find/${this.searchContent}`)
          .then(res=>{
            if(res.data.found){
              
              if(res.data.docs != ''){
                  //yo user bhanne array ma sabai data haru cha
                  this.user = res.data.docs;
                  this.showNotification1(false);
              }else{
                //alert('uers chahi payena')
                  this.user = [];
                  this.showNotification1(true);
              }
              
            }else{
              //alert("something is wrong")
            }
            
            
          })
          .catch(err=> alert(err));
          
      },
      logout(){
        localStorage.removeItem('usertoken')
      },
      showNotification(){
        
         //get notifications
        axios.get(`http://localhost:5000/users/notifications/${this.name}`)
          .then(res=>{
            if(res.data.success){
              this.notifications = res.data.docs;
            }
          })
          .catch(err => alert(err));
        var vm = this;
         vm.$refs.badge1.style.display='none';
         
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
        
        
      },
      showNotification1(value){
        var vm = this;
        if(value == true){
          
          vm.$refs.notificationid1.style.visibility = 'hidden';
          vm.$refs.notificationid1.style.height = '0px';
          vm.$refs.notificationid1.style.opacity = '0';
          
        }
          else
          {
            
            vm.$refs.notificationid1.style.visibility = 'visible'
            vm.$refs.notificationid1.style.opacity = '1';
            vm.$refs.notificationid1.style.height = 'auto';
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
#posticon{  
    border-radius: 50%;
    width: 40px;
    height: 40px;
    margin-right: 10px;
    vertical-align:middle ;
    border: 4px solid rgb(157, 255, 173);
  
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
  transition: 0.2s;
  
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
.dpdownbody li:hover{
  background-color: rgb(230, 230, 230);
  cursor: pointer;
}

#notificationid1{
 padding:10px;
  visibility: hidden;
  z-index: 1;
  position: absolute;
  top:60px;
  right: 50px;
  height:0px;
  width:300px;
  background-color: white;
  border: 1px solid green;
  opacity: 0;
  text-align:center;
  
}
.dpdownbody1 ul{
  list-style: none;
  margin: 0%;
  padding: 0%;
}
.dpdownbody1 li{
  border-bottom: 1px solid grey;
  padding: 10px;
}

.badge {
 
  padding: 1px 4px;
  border-radius: 50%;
  background: red;
  color: white;
  position: absolute;
  top: +10px;
  

  
}

.seemore{ 
  margin-top:5px;
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

