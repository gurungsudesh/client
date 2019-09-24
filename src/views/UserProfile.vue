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
  
}
.UPmainbody{
      position: absolute;
    left: 0%;
    margin-top:0%;
    width: 100%;
    height: 91%;
    background-color: white;
}

.UPtop{
  border-bottom: 2px solid green;
}
.UPltop{
    margin-top: 20px;
    padding-left: 10px;
    height: auto;
    padding-bottom: 20px;
    
    border-bottom: 1px solid lightgray;   
}
.UPlbottom{
    position: absolute;
    margin-top:10%;
    width: 80%;
    margin-left: 10%;
    background-color:rgb(228, 253, 228);
    border: 1px solid rgb(189, 218, 189);
    border-radius: 10px;
}
.UPleft{
    position: absolute;
    left: 0%;
    background-color: white;    
    width: 30%;
    height: 100%;
    border-right: 1px solid lightgrey;
    transition: 0.5s;

}
.UPright{
    position: absolute;
    right: 0%;
    width: 70%;
    height: 100%;
    background-color: white;
    transition: 0.5s;
}
@media only screen and (min-width : 0px) and (max-width: 800px) {
    .UPleft{
        opacity: 0;
    }
    .UPright{
        width: 100%;
    }
    
}
</style>