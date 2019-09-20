<template>
    <div>
        <div class="leftbody">
            <div class="topleft">
                <p id="compose">Compose Message</p>     
            </div>
            <div class="bottomleft" >
                <div  id="fromsearch">
                        <span style="margin-left:10px ;color:gray; font-size:20px;"><b>To</b></span>  <input class="form-control" id="inputtext" type="text"  aria-label="Search">
                </div>
                <div id="fromsearch">
                    <span style="margin-left:10px; color:gray; font-size:20px;"><b>Subject</b></span>
                    <form @submit="sendMessage()"  id="formmessage">
                            <textarea class="form-control"  id="sendm" rows="17" placeholder="Send the reply message" v-model="replyMessage"></textarea>
                            <button style="float:right;" type="submit" id="mbtn" class="btn btn-success" >Send</button>
                    </form>
                </div>
                
                
            </div>
    </div>
    <!-- -------  -->
    <div class="rightbody">
        <div class="topright">
                        <!-- <div  @click="sendData(item.sender)" class="messagingpeople" v-for="(item,index) in userData " :key="index"   style="width:100%">
                    <img src="../../../../images/ProfilePic.jpg"><span style="font-size: 20px"><b>
                        {{item.sender}}
                    </b></span>
                </div> -->
                <table id="tableinbox" class="table table-hover">
                    <thead>
                        <tr>
                        <th style="width:20%" scope="col">First</th>
                        <th style="width:70%" scope="col">Last</th>
                        <th style="width:10%" scope="col">Handle</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td ><b>Prashant Dhoju</b> </td>
                            <td >sssssssssssssssssssssssss</td>
                            <td ><b>date</b> </td>
                        </tr>
                       
                    </tbody>
                    
                </table>
            </div>

            </div>
        </div>
            

</template>
<script>
import axios from 'axios'
import jwtDecode from 'jwt-decode'
export default {
    name: "Messageshow",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
    return {
        name: decode.name,
        userData: [],
        userConversation: [],
        inConversationWith: '',
        replyMessage: '',
        // data1 : [{
        //             "id":0 ,
        //             "conversation_with":"Prashant Dhoju",
        //             "conversation_by":"Sudesh",
        //             "recentdate":"2015/2/3",
        //             "conversationstartedate":"2015/2/3"
        //         },
        //         {   "id":1 ,
        //              "conversation_with":"Sudesh Dhoju",
        //             "conversation_by":"Sudesh",
        //             "recentdate":"2015/2/3",
        //             "conversationstartedate":"2015/2/3"
        //         },
        //         {    "id":2 ,
        //              "conversation_with":"Shishir Dhoju",
        //             "conversation_by":"Pokemon",
        //             "recentdate":"2015/2/3",
        //             "conversationstartedate":"2015/2/3"
                    
        //         }]
        
    }
  },
  created(){
      //malai message pathako sabai users aaunu paryo 
      axios.get(`http://localhost:5000/users/messages/${this.name}`)
        .then(res=>{
            if(res.data.msg){
                this.userData = res.data.docs;
            }
        })
        .catch(err=> alert(err));
  },
  methods: {
      //tyo click gareko user sanga ko conversation nikane aaba
        sendData(sender){
           this.inConversationWith = sender;
            axios.get("http://localhost:5000/users/conversation", {Rname: this.name, Sname: this.inConversationWith , apple: "apple"})
                .then(res =>{
                    if(res.data.msg){
                        this.userConversation = res.data.docs;
                    }
                })
                .catch(err => alert(err));

        },
        whosend(value){
          if (value==this.name){
              return false;
          }
          else{
              return true;
          }
      },
      sendMessage(){
          axios.post(`http://localhost:5000/users/messages/${this.inConversationWith}`,{sname: this.name, content: this.replyMessage})
            .then(res=>{
                if(res.data.success){
                    alert("Message sent");
                    //getting all the messages
                    axios.get("http://localhost:5000/users/converstion",{rname: this.name, sname: this.inConversationWith })
                        .then(res=>{
                            if(res.data.msg){
                                this.userConversation = res.data.docs;
                            }
                        })
                        .catch(err => alert(err));
                }
                this.replyMessage = '';
            })
            .catch(err=> alert(err));
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
            border-bottom: 2px solid green;
            
        }
        #fromsearch{      
            margin-top:15px;
            margin-left: 5%;
            width: 90%;
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
        .topright{
        position: absolute;
        top:0px;
        width: 100%;
        height:100%;
        background-color: white;
        overflow:auto;
        padding: 10px;
    }
    .topright::-webkit-scrollbar {
        width: 10px;
    }
    .topright::-webkit-scrollbar-thumb:hover {
        background: green; 
    }
    .topright::-webkit-scrollbar-thumb {
        background: rgb(59, 163, 59); 
        border-radius: 10px;
    }
    .bottomright{
        border-top:1px solid green;
        position: absolute;
        top:88%;
        width: 100%;
        height: 12%;
        
        background-color: rgb(119, 218, 119);
    }
    .topright img{
            border-radius: 50%;
            width: 50px;
            height: 50px;
            border: 5px solid rgb(161, 230, 161);
        }
    #mbtn{
        
        border-radius: 20px;
        font-size: 18px;     
        margin-top:10px;
        padding:5px;
        padding-left: 20px;
        padding-right: 20px;
        
    }
    #sendm{
        width: 100%;
    }
    
    .status{
        background-color: lightgreen;
        padding: 10px;
        border-radius: 10px ;
        word-wrap:break-word;
        width: auto;
    }
    td{
        padding: 5px;
        word-wrap:break-word;
        word-break: break-all;
    }
    button{
        padding: 5px;
    }
    #sbtn{
        margin-left:-50px;
        background:none;
        border:none;
        
    }
    textarea{
        font-size: 15px;
        resize: none;
        border-radius: 10px;
        padding: 5px;
        overflow: hidden;
        border:2px solid lightgray;
    }
    .leftbody{
    position: absolute;
    left: 0px;
    top: 0px;
    height: 100%;
    width:30%;
    background-color: white;
    border-right: 1px solid green;
}
.rightbody{
    position: absolute;
    right: 0px;
    top: 0px;
    height: 100%;
    width:70%;
}
#inputtext{
    outline: none;
    border: 2px solid lightgray;
    border-radius: 10px;
    width:100%;
    
}
#compose{
    font-size:38px;
     height:100%;
     color:white;
    -webkit-text-stroke-width: 1.2px;
  -webkit-text-stroke-color: green;
   text-align:center;
    font-weight:bold;
   background-color:lightgreen;
}
#tableinbox{
    width:100%;
    background-color: rgb(245, 255, 245);
}
#tableinbox td{
    
    padding: 1px;
}
</style>