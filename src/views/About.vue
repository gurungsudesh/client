<template>
 <div class="pok" >
   <div class="mainbody">
   <div class="home-header">
    <NavBar/>
   </div>
   <div class="homebody">
      <div class="leftbody">
        <UserInfo/>
        <div class="hotposition">
          <HotTopics/>
        </div>
      </div>
      <div ref="mobleftid" id="mobleftid" class="mobleftbody">
            <div  ref="mtlsidenav"  id="mtlsidenav" class="mobleftcontent">
            <button style="margin-left:90%" @click="closeleftslide">+</button>
            <div class="animationslideleft">
            <UserInfo/>
            <HotTopics/>
            </div>
            </div>
            
              <div @click="openleftslide" id="leftslider" ref="leftslider" class="leftnav">
              <div id="leftsliderarrow">
                <i class="fas fa-arrow-right"></i>
              </div>
            </div>
                        
      </div>
     <div class="middlebody">
       
        <AddPost />
       
    
     </div>
      <div class="rightbody">
      <FollowRecom/>
      </div>
      <div ref="mobrightid" id="mobrightid" class="mobrightbody">
            <div  ref="mtrsidenav"  id="mtrsidenav" class="mobrightcontent">
            <button style="margin-left:90%" @click="closerightslide">+</button>
            <FollowRecom/>
            </div>
            
              <div @click="openrightslide" id="rightslider" ref="rightslider" class="rightnav">
              <div id="rightsliderarrow">
                <i  class="fas fa-arrow-right"></i>
              </div>
            </div>
                        
      </div>
  </div>
 </div>
 </div>  
</template>
<script>
import UserInfo from '../components/UserHome/UserInfo';
import NavBar from '../components/UserHome/NavBar';
import HotTopics from '../components/UserHome/HotTopics'
import AddPost from '../components/UserHome/AddPost';

import FollowRecom from '../components/UserHome/FollowRecom';
import jwtDecode from 'jwt-decode';


export default {
  
  data(){
     
    const token = localStorage.usertoken
    const decoded = jwtDecode(token)
    
    return {
      
      name: decoded.name,
      email: decoded.email,
     
    }
  },
  components: {
    UserInfo,
    NavBar,
    HotTopics,
    AddPost,
   
    FollowRecom
  },
  methods:{
    openleftslide(){
      var vm = this;
      vm.$refs.mtlsidenav.style.display = 'block';
      vm.$refs.leftslider.style.marginLeft='100%';
      vm.$refs.leftslider.style.width='5%';  
      vm.$refs.mobleftid.style.width='95%';
      vm.$refs.mobleftid.style.zIndex='1';
    },
    closeleftslide(){
      var vm = this;
      vm.$refs.mtlsidenav.style.display = 'none';
      vm.$refs.leftslider.style.marginLeft='0%';
      vm.$refs.leftslider.style.width='100%';
      vm.$refs.mobleftid.style.width='5%';
      vm.$refs.mobleftid.style.zIndex='0';
    },
    openrightslide(){
      var vm = this;
      vm.$refs.mtrsidenav.style.display = 'block';
      vm.$refs.rightslider.style.marginRight='100%';
      vm.$refs.rightslider.style.width='5%';  
      vm.$refs.mobrightid.style.width='95%';
      vm.$refs.mobrightid.style.zIndex='1';
    },
    closerightslide(){
      var vm = this;
      vm.$refs.mtrsidenav.style.display = 'none';
      vm.$refs.rightslider.style.marginRight='0%';
      vm.$refs.rightslider.style.width='100%';
      vm.$refs.mobrightid.style.width='5%';
      vm.$refs.mobrightid.style.zIndex='0';
    }
    
  }
}
</script>
<style scoped>

.mainbody{
  position: absolute;
  height: 100%;
  width: 100%;
  }
  .leftbody{
    position: absolute;
    left: 0%;
    height: 100%;
    width: 25%;
    
    
}
.home-header{
  border-bottom: 1px solid green;
}
.postclass{
  background-color: lightgray;
  
    padding-left: 3px;
    padding-right: 3px;
}
.middlebody{
    position: absolute;
    left: 25%; 
    background-color: white;
    width: 50%;
    border-bottom: 1px solid green;  
    border-right: 1px solid green;
     border-left: 1px solid green;
}
.middlebody::-webkit-scrollbar {
    width: 10px;
}
.middlebody::-webkit-scrollbar-thumb:hover {
  background: green; 
}
.middlebody::-webkit-scrollbar-thumb {
  background: rgb(59, 163, 59); 
  border-radius: 10px;
}
.rightbody{
    position: absolute;
    left: 75%;
    height: 100%;
    width: 25%;
}
.homebody{
  margin-top: 0%;
  background-color: white;
  height:90%;
  width:100%;
  position: absolute;
  left: 0%;
  border-radius: 20px;
}

#mobleftid{
  display: none;
}
#mobrightid{
  display: none;
}
.hotposition{
  margin-top:20%;
}
@media only screen and (max-width: 1000px) {
    .leftbody{
      display: none;
    }
    .rightbody{
      display: none;
    }
    .middlebody{
      position: absolute;
      left:5%;
      width: 90%;
    }
    .homebody{
      
      width: 100%;
    }
    #mobleftid{
      z-index: 0;
      display: block;
      position: absolute;
      left: 0%;
      height: 100%;
      width: 5%;
      
    }
    #mtlsidenav{
      display: none;
      position: absolute;
      width:100%;
      height: 100%;
      left: 0px;
      
      background-color: rgb(159, 226, 146);
      
    }
    #leftslider{
      position: absolute;
      left: 0%;
      top:45%;
      height: 10%;
      width: 100%;
      
      margin-left: 0px;
       
     
    }
    #leftsliderarrow{
      position: absolute;
      background-color: rgb(44, 160, 44);
      font-size: 3vw;
      padding-top:30px;
      padding-bottom: 30px;
      padding-left: 10%;
      padding-right: 10%;
      color: white;
    }
    #mobrightid{
      z-index: 0;
      display: block;
      position: absolute;
      right: 0%;
      height: 100%;
      width: 5%;
    }
    #mtrsidenav{
      display: none;
      position: absolute;
      width:100%;
      height: 100%;
      right: 0px;
      
      background-color: rgb(159, 226, 146);
      
    }
    #rightslider{
      
      position: absolute;
      right: 0%;
      top:45%;
      height: 10%;
      width: 100%;
      
       
     
    }
    #rightsliderarrow{
      transform: rotate(180deg);
      position: absolute;
      background-color: rgb(44, 160, 44);
      font-size: 3vw;
      padding-top:30px;
      padding-bottom: 30px;
      padding-left: 10%;
      padding-right: 10%;
      color: white;
    }

    
  
}
</style>
