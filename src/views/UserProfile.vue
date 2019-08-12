<template>
    <div>
        <h2>main</h2>
        <div class="UPmainbody">
            <div class="UPtop">
                <NavBar/>
            </div>
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
.UPmainbody{
  position: absolute;
  height: 100%;
  width: 100%;
  background-image: linear-gradient(to bottom,  rgb(255, 255, 255),rgb(228, 255, 230));
}
    

.UPtop{
  border-bottom: 2px solid green;
}
    
</style>