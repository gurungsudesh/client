<template>
    <div> 
        
                    <div class="followtext">
                        <div id="followtext1">
                           <h4><b>Who To Follow</b></h4> 
                           <ul class="list-group list-group-flush" v-for="(item,index) in users " :key="index">
                  
                            <li class="list-group-item"><img src="../../../images/ProfilePic.jpg" id="otherprofileicon" >{{item.name}}<form @submit="follow(name,id, item.name, item._id )"><button  type="submit" class="btn btn-success">Follow</button></form></li>
              
                 
                 
                          </ul>

                    </div>
                </div>
        

     
    </div>
   
</template>

<script>
import jwtDecode from 'jwt-decode'
import axios from 'axios';
export default {
    name: "FollowRecom",
    data(){
      const token = localStorage.usertoken
      const decode = jwtDecode(token)
      return{
        users: [],
        name: decode.name,
        id: decode._id
      }
    },
    created(){
      axios.get("http://localhost:5000/users/recommendation")
      
        .then(res =>{
          const array = res.data.docs;
          this.users = array.filter(user => user.name !== this.name)

        })
        .catch(err=> alert(err))
    },
    methods: {
      follow(name, userID, followName, followId){ 
        //alert("user ko : "+ name + " , " + userID +", follow garna lako: "+followName + ", "+followId)
       //if(){//
          axios.post("http://localhost:5000/users/follow", {name, userID, followName, followId})
          .then(res =>{
            if(res.data.docs.friend){
              alert("Followed")


            }
          })
          .catch(err=> alert(err));
       //}
       //else{
         //axios.post("http://localhost:5000/users/follow")
           //yaha chai unfollow garne mechanism banaune
         
      }
    }

    
    
}
</script>

<style scoped>
.followtext{
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
    text-align: center;
    
  }
  button{
   margin-top:1%;
   

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
