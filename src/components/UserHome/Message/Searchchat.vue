<template>
    <div>
        <div class="topleft">
            <form class="form-inline" id="fromsearch">
                    <input class="form-control" style="width: 250px" type="search" placeholder="Search" aria-label="Search">
                    <button id="sbtn" class="btn btn-success" type="submit"><i class="fas fa-search" ></i></button>
            </form>
        </div>
        <div class="bottomleft" >
            <div  @click="sendData(item.sender)" class="messagingpeople" v-for="(item,index) in userData " :key="index"   style="width:100%">
                <img src="../../../../images/ProfilePic.jpg"><span style="font-size: 20px"><b>
                    {{item.sender}}
                </b></span>
                <!-- yesma click garyo vane getmessage with sender=this.name and receiver=conversation.with an tyo chai side ma dekhaucha--> 
            </div>
            
        </div>
    </div>
</template>
<script>
import axios from 'axios'
import jwtDecode from 'jwt-decode'
export default {
    name: "Searchchat",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
    return {
        name: decode.name,
        userData: [],
        data1 : [{
                    "id":0 ,
                    "conversation_with":"Prashant Dhoju",
                    "conversation_by":"Sudesh",
                    "recentdate":"2015/2/3",
                    "conversationstartedate":"2015/2/3"
                },
                {   "id":1 ,
                     "conversation_with":"Sudesh Dhoju",
                    "conversation_by":"Sudesh",
                    "recentdate":"2015/2/3",
                    "conversationstartedate":"2015/2/3"
                },
                {    "id":2 ,
                     "conversation_with":"Shishir Dhoju",
                    "conversation_by":"Pokemon",
                    "recentdate":"2015/2/3",
                    "conversationstartedate":"2015/2/3"
                    
                }]
        
    }
  },
  created(){
      //getting all the messages of the user
    axios.get(`http://localhost:5000/users/messages/${this.name}`)
        .then(res=>{
            if(res.data.msg){
                this.userData = res.data.docs;
            }
        })
        .catch(err=> alert(err));


  },
  methods: {
      sendData(sender){
          this.$emit('sendData',sender)
      }
  }
    
}
</script>
<style scoped>
    .bottomleft img{
            border-radius: 50%;
            width: 50px;
            height: 50px;
            margin-right: 10px;
        }
        .topleft{
            position:absolute;
            top: 0px;
            width: 100%;
            height:10%;
            border-bottom: 1px solid green;
            
        }
        #fromsearch{
            position: absolute;
            margin-top:15px;
            margin-left: 20px;
        }
        .bottomleft{
            position: absolute;
            bottom:0px;
            height:90%;
            width:100%;
            padding: 5px;
           
        }
        .messagingpeople{
            width: 100%;
            background-color: rgb(192, 247, 175);
            margin-top: 5px;  
            border-radius: 10px;
            padding: 5px;
            color: rgb(29, 63, 32);
        }
        
        .messagingpeople:hover{
            background-color: rgb(170, 211, 156);
            cursor: pointer;
        }
        .messagingpeople:active{
            background-color: rgb(74, 129, 57);
            cursor: pointer;
        }
</style>