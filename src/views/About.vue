<template>
 <div class="pok" >
   <div class="mainbody">
   <div class="home-header">
    <NavBar/>
   </div>
   <div class="homebody">
      <div class="leftbody">
        <UserInfo/>
        <HotTopics />
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
    <!--Trying -->
    <!-- 
      <div>
       <table class="table col-md-6 mx-auto">
                <tbody>
                    <tr>
                        <td>Name</td>
                        <td>{{name}}</td>
                    </tr>
                    <tr>
                        <td>Email</td>
                        <td>{{email}}</td>
                    </tr>
                </tbody>
            </table>
    </div>
    -->
    <Posts/>
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
import Posts from '../components/UserHome/Posts';
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
    Posts,
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
  background-image: linear-gradient(to bottom,  rgb(255, 255, 255),rgb(228, 255, 230));
}
  .leftbody{
    position: absolute;
    left: 0%;
    height: 100%;
    width: 25%;
    
}
.home-header{
  border-bottom: 2px solid green;
}
.middlebody{
    position: absolute;
    left: 25%; 
    height: 100%;
    width: 50%;
    border-right: 1px solid rgb(204, 204, 204);
    border-left: 1px solid rgb(204, 204, 204);
    border-top: 1px solid rgb(204, 204, 204);
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
@media only screen and (max-width: 800px) {
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
      height: 100%;
      width: 100%;
      background-color: rgb(44, 160, 44);
      margin-left: 0px;
       
     
    }
    #leftsliderarrow{
      position: absolute;
      top:40%;
      font-size: 4vw;
      padding-left: 10%;
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
      height: 100%;
      width: 100%;
      background-color: rgb(44, 160, 44);
      margin-right: 0px;
       
     
    }
    #rightsliderarrow{
      transform: rotate(180deg);
      position: absolute;
      top:40%;
      font-size: 4vw;
      padding-right: 10%;
      color: white;
    }

    
  
}
</style>
