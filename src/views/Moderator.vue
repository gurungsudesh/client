<template>
    <div>
        <div class="mainbody">
            <div class="container">
                <div class="m_leftside" >
                    <UserInfo/>
                </div>
                <div class="m_rightside">
                    <Search/>
                    <Posts/>
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
        left: 25%;
        width: 75%;
        height: 100%;
        background-color: white;
}
    .m_leftside{
        position: absolute;
        left: 0%;
        background-color: white;    
        width: 25%;
        height: 100%;
        border-right: 1px solid lightgrey;
    
}
</style>
