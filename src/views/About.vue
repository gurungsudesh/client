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
     <div class="middlebody">
    <AddPost />
    <Posts/>
     </div>
      <div class="rightbody">
    <FollowRecom/>
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
export default {
  components: {
    UserInfo,
    NavBar,
    HotTopics,
    AddPost,
    Posts,
    FollowRecom

  }
}
</script>
<style scoped>
.mainbody{
  position: absolute;
  height: 100%;
  width: 100%;
  background-color: rgb(209, 209, 209);
}
  .leftbody{
    position: absolute;
    left: 3%;
    height: 90%;
    width: 20%;
}
.home-header{
    background-color: rgb(56, 0, 0);
    position: absolute;
    top: 0%;
    height: 10%;
    width: 100%;
    padding-left: auto;
    padding-right: auto;
    border-bottom: 2px solid white;
}
.middlebody{
    position: absolute;
    left: 25%;
    
    height: 90%;
    width: 50%;
}
.rightbody{
    position: absolute;
    left: 78%;
    
    height: 90%;
    width: 20%;
}
.homebody{
  margin-top: 5%;
}
</style>
