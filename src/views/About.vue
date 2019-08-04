<template>
  <div class="about">
    <h1>This is an about page</h1>
    <NavBar />
    <UserInfo/>
    <HotTopics />
    <AddPost />
    <Posts/>
    <FollowRecom/>
    
    
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
  
</style>
