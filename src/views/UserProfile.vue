<template>
    <div>
        <div class="UPmainpage">
            <div class="UPtop">
                <NavBar/>
            </div>
            <div class="UPmainbody">  
                <div class="UPleft">
                    <div class="UPltop">
                        <UPInfo/>
                    </div>
                    <div class="UPlbottom">
                        <UPBio/>
                    </div>
                </div>
                <div class="UPright">
                    <UPTimeline/>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import NavBar from '../components/UserHome/NavBar';
import UPBio from '../components/UserHome/UserProfile/UP_Bio';
import UPInfo from '../components/UserHome/UserProfile/UP_Info';
import UPTimeline from  '../components/UserHome/UserProfile/UP_Timeline';
export default {
    name: "userprofile",
    components: {
    UPBio,
    NavBar,
    UPInfo,
    UPTimeline
  }
}

</script>
<style scoped>

.UPmainpage{
  position: absolute;
  height: 100%;
  width: 100%;
  background-image: linear-gradient(to bottom,  rgb(255, 255, 255),rgb(228, 255, 230));
}
.UPmainbody{
      position: absolute;
    left: 0%;
    margin-top:0%;
    width: 100%;
    height: 90%;
    background-color: greenyellow;
}

.UPtop{
  border-bottom: 2px solid green;
}
.UPltop{
    margin-top: 20px;
    padding-left: 10px;
    border-bottom: 1px solid lightgray;
    height: 30%;
    
}
.UPlbottom{
    position: absolute;
    top:40%;
    width: 80%;
    height: 55%;
    margin-left: 10%;
    background-color:rgb(159, 255, 159);
    border-radius: 20px;
}
.UPleft{
    position: absolute;
    left: 0%;
    background-color: white;    
    width: 30%;
    height: 100%;
    border-right: 1px solid lightgrey;

}
.UPright{
    position: absolute;
    left: 30%;
    width: 70%;
    height: 100%;
    background-color: white;
}

    
</style>