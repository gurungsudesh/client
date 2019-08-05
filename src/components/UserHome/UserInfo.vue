<template>
    <div> 
      
                <div class="profileinfo">
                    
                    <div class="profilename">
                        <div id="profilename1">
                        <img src="bullet.jpg" id="profileicon" >Someone Gurung<!--{{username}}-->
                    </div>
                    </div>
                    <div class="followerinfo">
                            <table id="tables">
                                    <tr>
                                      <th>Post</th>
                                      <th>Followers</th> 
                                      <th>Followings</th>
                                    </tr>
                                    <tr>
                                      <td>Eve</td>
                                      <td>Jackson</td> 
                                      <td>94</td>
                                    </tr>
                                  </table>
                        
                    </div>
                    
                        
                    </div>
    </div>
</template>

<script>
export default {
    name : "UserInfo"
}
</script>

<style scoped>
.profileinfo{
    width: 100%;
    height: 30%;
    color: white;
    background-color: white;
    border-radius: 25px;
   
   box-shadow: 8px 8px 4px grey;
}

#profilename1{
    font-family: Arial, Helvetica, sans-serif;
    padding:10px;
   
    font-size: 20px;
    font-weight: 100;
    
    
}
.profilename{
    background-color: rgb(49, 173, 49);
    width: 100%;
    height: 40%;
    border-radius: 20px;
    
}
#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-right: 10px;
    vertical-align:middle;
    border: 3px solid darkgrey;
   
   
}

#tables th,#tables  td {
    padding: 10px;
    text-align: center;
    font-size: 15px;
   
  }
  #tables{
    
    padding: 20px;
    width: 100%;
    color: black;
}
</style>
