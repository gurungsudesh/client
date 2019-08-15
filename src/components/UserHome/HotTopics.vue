<template>
    <div> 
         <div class="hottopic">
           
            <div id="hotcontent">
               <ul class="list-group list-group-flush">
                  <li class="list-group-item"> <h4><b>Hot topics</b></h4> </li>
                  <li class="list-group-item">Topics 2</li>
                 <li class="list-group-item">Topics 3</li>
                 <li class="list-group-item">Topics 4</li>
                 <li class="list-group-item">Topics 5</li>
                  <li class="list-group-item">Topics 6</li>
            </ul>
                        </div>
                        </div>
                        
                
               
    </div>
</template>

<script>
export default {
    name: "HotTopics"
}
</script>

<style scoped>

  .hottopic{
      margin: 20px;
      border-radius: 20px;
      width: 80%;
    background-color: rgb(199, 255, 199);
       
      
    
  }
  ul{
    border-radius: 10px;
  }
  li{
    background-color: rgb(199, 255, 199);
    border-radius: 10px;
  }
  #hotcontent{
      font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    font-size:15px;
    padding:5%;
  
   color: black;
    
  }
 
</style>
