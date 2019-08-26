<template>
    <div>
        <div class="noti_body">
            <div class ="noti_title">
                <div id="noti_title1">
                    Notifications
                </div>
            </div>
            <div class="noti_noti">
                <div id="noti_noti1">
                        <table  id="tables3">
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " > Someone has just Posted</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">Time</td>
                                </tr>
                        </table>
                        <table  id="tables3">
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " > Someone has just Posted</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">Time</td>
                                </tr>
                        </table>
                        <table  id="tables3">
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " > Someone has just Posted</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">Time</td>
                                </tr>
                        </table>
                        <table  id="tables3">
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " > Someone has just Posted</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">Time</td>
                                </tr>
                        </table>
                        <table  id="tables3">
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " > Someone has just Posted</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">Time</td>
                                </tr>
                        </table>
               
            </div>

            </div>
        </div>
    </div>

</template>

<script>
export default {
    name:'noticontent'
}
</script>

<style scoped>
.noti_body{
     background-color: white;
    width:70% ; 
    padding: 10px; 
    position: absolute;
    left:10%;
    margin-top:2%;
    border: 1px solid green;
    
 }
 .noti_title
 {
    border-bottom: 1px solid black;
 } 
 #noti_title1{
     margin-left: 2%;
     margin-bottom: 10px;
     text-align: left;
     font-size: 25px;
     font-weight: bold;
     color: green ;
 }
#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   
   vertical-align:middle  ;
   border: 3px solid rgb(146, 209, 150);
 
}
#tables3{
  margin-top:5px;
   background-color: rgb(235, 235, 235);
  
}
  
</style>