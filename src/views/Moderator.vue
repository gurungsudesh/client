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
    height:9%;
    width: 100%;
}
.bottomright{
    position: absolute;
    top:9%;

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
</style>
