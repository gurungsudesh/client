<template>
    <div class="container">             
         <div class="writepost" >
         <div id="writepost1">
                                
              <form action="" id="form1" >

                  <div class="form-row">
                    <div class="form-group col-md-1.5">
                         <img src="bullet.jpg" id="profileicon">   
                    </div>
                    <div class="form-group col-md-9">          
                  <div class="form-group shadow-textarea">
                     <textarea class="form-control z-depth-1" style="font-size:15px" id="exampleFormControlTextarea6" rows="3" v-model="postdata" placeholder="Write something here..."></textarea>
                    </div>
                 </div>
              <div class="form-group col-md-1">
                <button style="margin-top:10px" class="btn btn-success" @click="addItem(postdata)" >Post</button>
                 </div>
                 </div>
            </form>
                                
                                
      </div>
     </div>
        
    </div>
</template>

<script>
export default {
    name: "AddPost"
}
</script>

<style scoped>
.container{
    border-bottom: 10px solid lightgrey;
}
.writepost{
    margin-top: 10px;
    width: 100%;
   
    
    
}
#writepost1{
    padding: 4px;
}

#Imageinserticon{
   margin-right: 10px;
    margin-left: 10px;
    vertical-align:bottom;
    padding-bottom: 5px;
    border: 2px solid rgb(146, 209, 150);
   
}
#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-right: 10px;
    vertical-align:middle;
    border: 5px solid rgb(146, 209, 150);
   
   
}
</style>
