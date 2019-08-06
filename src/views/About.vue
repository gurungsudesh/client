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
  background-image: linear-gradient(to bottom, rgb(177, 255, 181), rgb(255, 255, 255));
}
  .leftbody{
    position: absolute;
    left: 0%;
    height: 100%;
    width: 25%;
    border-right: 2px solid rgb(207, 207, 207);
}
.home-header{
  border-bottom: 2px solid green;
}
.middlebody{
    position: absolute;
    left: 25%; 
    height: 100%;
    width: 50%;
    border-right: 2px solid rgb(204, 204, 204);
}
.rightbody{
    position: absolute;
    left: 75%;
    height: 100%;
    width: 22%;
}
.homebody{
  margin-top: 3%;
  background-color: white;
  height:80%;
  width:90%;
  position: absolute;
  left: 5%;
  border-radius: 20px;
}
</style>
