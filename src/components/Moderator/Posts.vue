<template>
    <div>
        <div class="container">
            <div class="postfeed" v-for="(item,index) in data1 " :key="index">
                <PostStats/>
                <PostContent/>
            </div>
        </div>
    </div>
</template>

<script>
import PostStats from "../Moderator/Post/PostStats"
import PostContent from "../Moderator/Post/PostContent" 
export default {
    name: "Posts"

}
</script>
<style scoped>
 .postfeed{
    margin-top: 10px;
   
    width: 50%;
    color: black;
    background-color: white;
    border-radius: 20px;
    border-bottom: 4px solid gray;
   

}
</style>

