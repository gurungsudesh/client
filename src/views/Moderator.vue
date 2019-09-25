<template>
    <div>
        <div class="mainbody">
                <div class="m_leftside" >
                    <UserInfo/>
                </div>
                <div class="m_rightside">
                   <div class="topright" style="border-bottom: 1px solid lightgrey">
                    <Search/>
                   </div>
                   <div class="bottomright">
                       <div class="firsthalf">
                        <Posts/>
                       </div>
                        <div class="secondhalf">
                            <UsersList/>
                        </div>
                   </div>
                
            </div>
        </div>
    </div>
</template>

<script>    
import Posts from "../components/Moderator/Posts"
import Search from '../components/Moderator/Search'
import UserInfo from '../components/Moderator/UserInfo'
import UsersList from '../components/Moderator/UsersList'
export default {
    name: "Moderator",
    components: {
        UserInfo,
        Search,
        Posts,
        UsersList
    },
    data(){
      return{
           t: localStorage.moderatorToken
      }
  },
    created(){
        if(!this.t){
        this.$router.push("/");
        }
    }
}
</script>

<style scoped>
    .m_rightside{
    
        position: absolute;
       right: 0%;
        width: 80%;
        height: 100%;
        background-color: white;
        transition: 0.5s;
}
    .m_leftside{
        position: absolute;
        left: 0%;
        background-color: white;    
        width: 20%;
        height: 100%;
        border-right: 1px solid lightgrey;
        transition: 0.5s;
    
}
.topright{
    position: absolute;
    top:0%;
    height:9%;
    width: 100%;
    
}
.bottomright{
    
    position: absolute;
    top:60px;

    width: 100%;
    background-color: rgb(235, 235, 235);   
}
.firsthalf{
    position:absolute;
    left: 0px;
    width:70%;
    height:auto;
    border: 1px solid lightgrey;
    
    
}
.secondhalf{
    position: absolute;
    right: 0px;
    width:30%;
    height: auto;
    border:1px solid lightgray;
    
}
@media only screen and (max-width: 1100px) {
    .m_leftside{
        opacity: 0;
        visibility: hidden;
    }
    .m_rightside{
        width: 95%;
    }
}
</style>
