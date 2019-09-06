<template>
    <div>
        <div class="fullbody">
            <div class="home-header"> 
                <NavBar/>
            </div>
            <div class="mainbody">
                <div class="leftbody">
                    <Searchchat/>
                </div>
                <div class="rightbody">
                    <Readchat/>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import NavBar from '../components/UserHome/NavBar';
import Searchchat from '../components/UserHome/Message/Searchchat';
import Readchat from '../components/UserHome/Message/Readchat';
export default {
    name: "message",
    components: {
    NavBar,
    Searchchat,
    Readchat
  },
  }
</script>
<style scoped>
.home-header{
  border-bottom: 1px solid green;
}
.fullbody{
    position: absolute;
    height: 100%;
    width: 100%;
}
.mainbody{
    position:absolute;
    left: 10%;
    width: 80%;
    height: 91%;
}
.leftbody{
    position: absolute;
    left: 0px;
    top: 0px;
    height: 100%;
    width:30%;
    background-color: red;
}
.rightbody{
    position: absolute;
    right: 0px;
    top: 0px;
    height: 100%;
    width:70%;
    background-color: green;

}
    
</style>