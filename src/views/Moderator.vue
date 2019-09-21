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
                           
                            <div id="followtext1">
                                <ul class="list-group list-group-flush" v-for="(item,index) in followers" :key="index">
                        
                                    <li class="list-group-item">
                                    
                                        <img src="../../images/ProfilePic.jpg" id="otherprofileicon" >
                                        {{item.followedBy}}                                        
                                        <button  class="btn btn-success" id="followbtn">Delete</button>
                                        
                                    
                                    </li>    
                                </ul>
                            </div>
                
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
export default {
    name: "Moderator",
    components: {
        UserInfo,
        Search,
        Posts
    }
}
</script>

<style scoped>
    .m_rightside{
    
        position: absolute;
        left: 20%;
        width: 80%;
        height: 100%;
        background-color: white;
}
    .m_leftside{
        position: absolute;
        left: 0%;
        background-color: white;    
        width: 20%;
        height: 100%;
        border-right: 1px solid lightgrey;
    
}
.topright{
    position: absolute;
    top:0%;
    height:11%;
    width: 100%;
}
.bottomright{
    position: absolute;
    top:11%;

    width: 100%;
    background-color: rgb(235, 235, 235);   
}
.firsthalf{
    position:absolute;
    left: 0px;
    width:50%;
    height:auto;
    border: 1px solid lightgrey;
    
    
}
.secondhalf{
    position: absolute;
    right: 0px;
    width:50%;
    height: auto;
    border:1px solid black;
    
}
#followbtn{
    background-color: white;
    color: green;
    border-radius: 20px;
    font-weight: bold;
    border: 2px solid green;
    float: right;
    width: 100px;
}

#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   vertical-align:top  ;
   border: 3px solid darkgrey;
 
}
</style>
