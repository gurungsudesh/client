<template>
    <div>
        <div class="fullbody">
            <div class="home-header"> 
                <NavBar/>
            </div>
            <div class="mainbody">
                <div class="leftbody">
                    <!--eta chai search ani v-for garera name haru dekhauni-->
                    <Searchchat/>
                </div>
                <div class="rightbody">
                    <!--eta chai sending ra comment dekhauni tyo chai v-for hanni ho-->
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
    background-color: rgb(215, 255, 215);
}
.mainbody{
    position:absolute;
    left: 10%;
    width: 80%;
    height: 91%;
    border-right: 2px solid green;  
    border-left: 2px solid green;
}
.leftbody{
    position: absolute;
    left: 0px;
    top: 0px;
    height: 100%;
    width:30%;
    background-color: white;
    border-right: 1px solid green;
}
.rightbody{
    position: absolute;
    right: 0px;
    top: 0px;
    height: 100%;
    width:70%;
}
    
</style>