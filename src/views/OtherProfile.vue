<template>
    <div>
        <div class="UPmainpage">
            <div class="UPtop">
                <NavBar/>
            </div>
            <div class="UPmainbody">  
                <div class="UPleft">
                    <div class="UPltop">
                        <OPInfo :msg="name" :msgid ="id"/>
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
          id:'',
      }
  },
  created(){
      this.name = this.$route.params.name;
        this.id=this.$route.params.id;
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

}
.UPright{
    position: absolute;
    left: 30%;
    width: 70%;
    height: 100%;
    background-color: white;
}

    
</style>