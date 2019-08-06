<template>
    <div> 
        
                    <div class="followtext">
                        <div id="followtext1">
                           <ul class="list-group list-group-flush">
                  <li class="list-group-item"> <h4><b>Who To Follow</b></h4> </li>
                  <li class="list-group-item"><img src="bullet.jpg" id="otherprofileicon" >ABC Gurung<button class="btn btn-success">Follow</button></li>
                 <li class="list-group-item"><img src="bullet.jpg" id="otherprofileicon" >ABC Gurung<button class="btn btn-success">Follow</button></li>
                 <li class="list-group-item"><img src="bullet.jpg" id="otherprofileicon" >ABC Gurung<button class="btn btn-success">Follow</button></li>
                 
                 
            </ul>

                    </div>
                </div>
        

     
    </div>
   
</template>

<script>
export default {
    name: "FollowRecom"
}
</script>

<style scoped>
.followtext{
      margin: 20px;
      border-radius: 20px;
      width: 100%;
    background-color: rgb(230, 230, 230);
       
      
    
  }
  ul{
    border-radius: 10px;
  }
  li{
    background-color: rgb(230, 230, 230);
    border-radius: 10px;
    text-align: center;
  }
  button{
    position: relative;
   

  }
  #followtext1{
      font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    font-size:15px;
    padding:5%;
  
   color: black;
    
  }
 
#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   
   vertical-align:middle  ;
   border: 3px solid rgb(146, 209, 150);
 
}
button{
  border-radius: 20px;
  width:70%;
}

</style>
