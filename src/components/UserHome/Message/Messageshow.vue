<template>
    <div>
        <div class="leftbody">
            <div class="topleft">
                <p id="compose">Compose Message</p>     
            </div>
            <div class="bottomleft" >
                <div  id="fromsearch">
                        <span style="margin-left:10px ;color:gray; font-size:20px;"><b>To</b></span>  <input class="form-control" id="inputtext" type="text" v-model="receivingUser" aria-label="Search">
                </div>
                <div id="fromsearch">
                    <span style="margin-left:10px; color:gray; font-size:20px;"><b>Message Content</b></span>
                    <form @submit="sendMessage(replyMessage)"  id="formmessage">
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
                        <th style="width:20%" scope="col">Sent by</th>
                        <th style="width:70%" scope="col">Content</th>
                        <th style="width:10%" scope="col">Date</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- <tr v-for="item in item"> -->
                        <tr v-for="item in allMessages" :key="item">
                            
                            <td ><b>{{item.sender}}</b> </td>
                            <td >{{item.message}}</td>
                            <td ><b>{{item.date}}</b> </td>
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
        replyMessage: '',
        receivingUser: '',
        allMessages: []
        // allMessages:[
        //     {
        //         sender: "apple",
        //         message: "message yo hai",
        //         date: "2019/20/20"
        //     }
        // ]

        
    }
  },
  created(){
      //getting the messages when im  the receiver
      axios.get(`http://localhost:5000/users/messagereceived/${this.name}`)
        .then(res=>{
            if(res.data.success){
                //alert('message get gareko')
                this.allMessages = res.data.docs;
                // getting the messages when im the sender
            axios.get(`http://localhost:5000/users/messagesent/${this.name}`)
                .then(res=>{
                    if(res.data.success){
                       this.allMessages = this.allMessages.concat(res.data.docs);
                       this.allMessages.sort(function(a,b){
                                return new Date(b.date) - new Date(a.date);
                            });
                    }
                })
                .catch(err => alert(err));
            }
        })
        .catch(err=> alert(err));
        
    

  },
  methods: {
    sendMessage(message){
        axios.post(`http://localhost:5000/users/sendmessage/${this.receivingUser}`, {sname: this.name, content: message})
            .then(res=>{
                if(res.data.success){
                    alert("message sent")
                    this.receivingUser = '';
                    this.replyMessage = '';
                      //getting the messages when im  the receiver
                        axios.get(`http://localhost:5000/users/messagereceived/${this.name}`)
                            .then(res=>{
                                if(res.data.success){
                                    //alert('message get gareko')
                                    this.allMessages = res.data.docs;
                                    // getting the messages when im the sender
                                axios.get(`http://localhost:5000/users/messagesent/${this.name}`)
                                    .then(res=>{
                                        if(res.data.success){
                                        this.allMessages = this.allMessages.concat(res.data.docs);
                                        }

                                    })
                                    .catch(err => alert(err));
                                }
                            })
                            .catch(err=> alert(err));
        
                    
                }
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
    
    padding: 10px;
}
</style>