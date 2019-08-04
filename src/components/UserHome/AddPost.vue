<template>
    <div> 
        <div class="newsfeed">
                    
                            <div class="writepost" >
                                <div id="writepost1">
                                
                                <form action="" id="form1" >
                                       <img src="bullet.jpg" id="profileicon">
                                    <input type="text" v-model="postdata"  >
                                    <img src="bullet.jpg" id="Imageinserticon" >
                                    <button type ="button" @click="addItem(postdata)" >Post</button>
                                   

                                  </form>
                                
                                
                            </div>
                        </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "AddPost"
}
</script>

<style>
.newsfeed{
    margin-top: 2%;
   
    width: 100%;
   
   
    
    box-shadow: 3px 3px 3px grey;
   
}
.writepost{
    background-color: rgb(56, 0, 0);
    width: 100%;
    height: 12%;
    border-radius: 15px;
    
}
#writepost1{
    padding: 4px;
}
#form1 input[type=text]{
width: 70%;
padding: 10px;
margin: 0%;
}
#Imageinserticon{
   margin-right: 10px;
    margin-left: 10px;
    vertical-align:middle;
    padding-bottom: 5px;
    border: 2px solid darkgrey;
   
}
#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-right: 10px;
    vertical-align:middle;
    border: 3px solid darkgrey;
   
   
}
</style>
