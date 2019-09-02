<template>
    <div>
        <div class="UPmainpage">
            <div class="UPtop">
                <NavBar/>
            </div>
            <div class="UPmainbody">  
                <div class="UPleft">
                    <div class="UPltop">
                        <OPInfo :msg="name" :cond ="status"/>
                    </div>
                    <div class="UPlbottom">
                        <OPBio :msg="name" />
                    </div>
                </div>
                <div class="UPright">
                    <OPTimeline :msg="name"/>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import NavBar from '../components/UserHome/NavBar';
import OPBio from '../components/UserHome/OtherProfile/OP_Bio';
import OPInfo from '../components/UserHome/OtherProfile/OP_Info';
import OPTimeline from  '../components/UserHome/OtherProfile/OP_Timeline';
export default {
    name: "otherprofile",
    components: {
    OPBio,
    NavBar,
    OPInfo,
    OPTimeline
  },
  data(){
      return{
          name: '',
          status: '',
      }
  },
  created(){
      this.name = this.$route.params.name;
      this.status = this.$route.params.status;
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