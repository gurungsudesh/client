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
                  <div v-for="(item,index) in notifications " :key="index">
                        <table  id="tables3"  v-if="(checkname(item.sender))" >
                                <tr>
                                  <td rowspan="2" style="padding-left:10px; width:40px; height:50px;" ><img src="../../../../images/ProfilePic.jpg" align="left" id="otherprofileicon"></td>
                                  <td style="width:100%; font-size: 15px; " ><b>{{item.sender}}</b> {{`${switching(item.type)}`}}</td> 
                                </tr>
                                <tr>
                                  <td style="color:grey; font-size: 12px;">{{item.date}}</td>
                                </tr>
                        </table>
                  </div>
            </div>

            </div>
        </div>
    </div>

</template>

<script>
import jwtDecode from 'jwt-decode'
import axios from 'axios'
export default {
    name:'noticontent',
    data(){
      const token = localStorage.usertoken
      const decode = jwtDecode(token)
      return{
        name: decode.name,
        notifications: []
      }
    },
    created(){
      axios.get(`http://localhost:5000/users/notifications/${this.name}`)
          .then(res=>{
            if(res.data.success){
              this.notifications = res.data.docs;
            }
          })
          .catch(err => alert(err));
    },
    methods:{
      checkname(value){
        if(value==this.name){
          return false;
        }
        else{
          return true;
        }
      },
      switching(value){
        switch(value){
         case "1":
            return("liked your post.");

          case "2":
             return("commented on your post.");
            
          case "3":
             return("has followed you.");
            
            case "4":
             return("has unfollowed you.");
            
        }
      }
    }
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