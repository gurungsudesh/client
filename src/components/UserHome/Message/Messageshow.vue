<template>
    <div>
        <div class="leftbody">
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
    <div class="rightbody">
        <div class="topright">
                        <table v-for="(item,index) in userData " :key="index"   style="width:100%">
                        
                            <tr v-if="(whosend(item.sender))">
                                <td style="width: 10%">
                                        <img src="../../../../images/ProfilePic.jpg">
                                </td>
                                <td style="width: 80%; text-align: left">
                                    <div ><label class="status">{{item.message}}</label></div>
                                </td>
                                <td style="width: 10%">

                                </td>
                            </tr>
                            <tr v-else>
                                <td>
                                        
                                </td>
                                <td style="width: 80%; text-align: right">
                                        <div ><label class="status" style="margin-left:50px;">{{item.message}}</label></div>
                                </td>
                                <td style="width: 10%">
                                        <img src="../../../../images/ProfilePic.jpg">
                                </td>
                            </tr>
                        
                        </table>
                        
                    </div>
                    <div class="bottomright">
                            <form class="form-inline" id="formmessage">
                                    <textarea class="form-control"  id="sendm" placeholder="message.." v-model="replyMessage"></textarea>
                                    <button id="mbtn" class="btn btn-success" @click="sendmessage(replyMessage)" >Send</button>
                            </form>
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
        axios.get("http://localhost:5000/users/converstion",{rname: this.name, sname: this.inConversationWith })
        .then(res=>{
            if(res.data.msg){
                this.userData = res.data.docs;
            }
        })
        .catch(err => alert(err));


  },
  methods: {
      sendData(sender){
          this.$emit('sendData',sender)
      },
      whosend(value){
          if (value==this.name){
              return false;
          }
          else{
              return true;
          }
      },
      /*sendmessage(msg){
        axios.post(`http://localhost:5000/users/messages/${this.inConversationWith}`,{sname: this.name, content: this.replyMessage})
            .then(res=>{
                if(res.data.success){
                    //getting all the messages
                    axios.get("http://localhost:5000/users/converstion",{rname: this.name, sname: this.inConversationWith })
                        .then(res=>{
                            if(res.data.msg){
                                this.userData = res.data.docs;
                            }
                        })
                        .catch(err => alert(err));
                }
                this.replyMessage = '';
            })
            .catch(err=> alert(err));
        //   this.data1.push({ id:this.data1.length, sender:this.name, receiver:'blalala' , message:value})
        //   this.omessage='';
      }*/
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
        .topright{
        position: absolute;
        top:0px;
        width: 100%;
        height:88%;
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
        margin-left:10px;
        padding: 10px;
    }
    #sendm{
        width: 90%;
    }
    #formmessage{
        margin: 10px;
        
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
    textarea{
        font-size: 15px;
        resize: none;
        border-radius: 10px;
        padding: 5px;
        overflow: hidden;
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
</style>