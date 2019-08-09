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
    <!--Trying -->
    <div>
       <table class="table col-md-6 mx-auto">
                <tbody>
                    <tr>
                        <td>First Name</td>
                        <td>{{username}}</td>
                    </tr>
                    <tr>
                        <td>Email</td>
                        <td>{{email}}</td>
                    </tr>
                </tbody>
            </table>
    </div>
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
import jwtDecode from 'jwt-decode'
import NavBar from '../components/UserHome/NavBar';
import HotTopics from '../components/UserHome/HotTopics'
import AddPost from '../components/UserHome/AddPost';
import Posts from '../components/UserHome/Posts';
import FollowRecom from '../components/UserHome/FollowRecom';


export default {
  data(){
    const token = localStorage.usertoken
    const decoded = jwtDecode(token)
    return{
      username : decoded.username,
      email : decoded.email
    }
  },
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
    width: 22%;
}
.homebody{
  margin-top: 3%;
  background-color: white;
  height:85%;
  width:95%;
  position: absolute;
  left: 2%;
  border-radius: 20px;
}
</style>
