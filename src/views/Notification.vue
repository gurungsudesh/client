<template>
    <div>
        <div class="mainbody">
            <div class="home-header">
                <NavBar/>
            </div>
            <div class="homebody">
                <Noticontent/>
            </div>
        </div>
    </div>

</template>

<script>
import NavBar from '../components/UserHome/NavBar'
import Noticontent from '../components/UserHome/Notification/Noticontent'
export default {
    name:'Notification',
    components: {NavBar,Noticontent}
}
</script>

<style scoped>
.mainbody{
    height: 100%;
    width: 100%;
    
}
.home-header{
  border-bottom: 1px solid green;
}
.homebody{
    
    position: absolute;
    height:91%;
    width: 100%;
    background-color: rgb(209, 255, 209);
}
</style>