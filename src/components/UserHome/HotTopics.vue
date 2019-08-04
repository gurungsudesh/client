<template>
    <div> 
         <div class="hottopic">
                        <div class="hottopic1" >
                            <div id="hotcontent">
                            Hot Topics
                        </div>
                        </div>
                        <div class="followerinfo">
                            <table id="tables">
                                    <tr>
                                      <td>Topic 1</td>
                                      
                                    </tr>
                                    <tr>
                                      <td>Topic 2</td>
                                      
                                    </tr>
                                    <tr>
                                      <td>Topic 3</td>
                                      
                                    </tr>
                                    <tr>
                                      <td>Topic 4</td>
                                      
                                    </tr>
                                  </table>
                        </div>
                
                </div>
    </div>
</template>

<script>
export default {
    name: "HotTopics"
}
</script>

<style>
#tables{
    
    padding: 20px;
    width: 100%;
    color: black;
}

#tables th,#tables  td {
    font-family: Arial, Helvetica, sans-serif;
    padding: 8px;
    text-align: center;
    font-size: 15px;
   
  }
  .hottopic{
      background-color: white;
      border-radius: 20px;
      width: 100%;
      height: 40%;
      margin-top: 15%;
       box-shadow: 8px 8px 4px grey;
      
    
  }
  .hottopic1{
      background-color: rgb(56, 0, 0);
      border-radius: 20px;
      width: 100%;
      height: 20%;
      

  }
  #hotcontent{
      font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    font-size:20px;
    padding:5%;
    color: white;
    
  }
  .followerinfo{
    background-color: white;
    width: 100%;
  
    border-radius: 20px;
    
}
</style>
