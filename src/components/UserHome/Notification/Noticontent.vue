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
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
                                <tr >
                                  <td width=20px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="text-align: left">Someone has just posted</td> 
                                </tr>
               
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
     margin-top: 2%;
     background-color: white;
    position: absolute;
    left: 10%;
    
    
    height: 80%;
    width: 80%;
    border-radius: 20px;
    border-bottom: 5px solid gray;
 }
 .noti_title
 {
    border-bottom: 2px solid black;
 } 
 #noti_title1{
     margin-left: 5%;
     margin-top: 3%;
     margin-bottom: 1%;
     text-align: left;
     font-size: 20px;
     font-weight: bold;
     color: rgb(56, 0, 0);
 }

</style>