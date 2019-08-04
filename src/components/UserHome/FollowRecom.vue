<template>
    <div> 
        <div class="whomtofollow">
                    <div class="followtext">
                        <div id="followtext1">
                            Whom to Follow?
                        </div>
                    </div>
                    <div class= "followtable">
                            
                                    <table   id="tables2">
                                            <tr >
                                              <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                              <td style="text-align: left">ABC Gurung</td> 
                                            </tr>
                                            <tr >
                                              <td><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                              <td style="text-align: left">ABC Gurung</td> 
                                            </tr>
                                            <tr >
                                              <td><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                              <td style="text-align: left">ABC Gurung</td> 
                                            </tr>
                                          </table>
                               
                            

                    </div>
                </div>

            </div>
   
</template>

<script>
export default {
    name: "FollowRecom"
}
</script>

<style>
.whomtofollow{
    margin-top: 100px;
    width: 100%;
    height: 45%;
    color: white;
    background-color: white;
    border-radius: 20px;
    box-shadow: 8px 8px 4px grey;
    
}
.followtext{
    background-color: rgb(56, 0, 0);
      border-radius: 20px;
      width: 100%;
      height: 20%;
}
#followtext1{
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    padding:20px;
    
    font-size: 20px;
    font-weight: 100;
}
#tables2 th,#tables2 td {
    font-family: Arial, Helvetica, sans-serif;
  padding: 10px;
  text-align: left;
  font-size: 15px;
 
}
#tables2{
    
    width: 100%;
    color: black;
    border-collapse: collapse;
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
