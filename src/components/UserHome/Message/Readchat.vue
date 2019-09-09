<template>
    <div>
        <!-- tyo conversation ma click garyo vane get garcha message-->
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
</template>
<script>
import jwtDecode from 'jwt-decode'
import axios from 'axios'
export default {
    name: "Readchat",
    props: ['value'],
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
    return {
        replyMessage:'',
        name: decode.name,
        //name:'Pokemon',
        inConversationWith: this.value,
        userData: [],
        data1 : [{
                    "id":0 ,
                    "sender":"Prashant Dhoju",
                    "receiver":"Pokemon",
                    "message":"asdasdasaPokemonsssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssadasssssssssssssssssssssssss",
                    
                },
                {   "id":1 ,
                    "sender":"Pokemon",
                    "receiver":"Prashant Dhoju",
                    "message":"saPokemosssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssn"
                },
                {    "id":2 ,
                    "sender":"Prashant Dhoju",
                    "receiver":"Pokemon",
                    "message":"saPokemon"
                }]
        
    }
  },
  created(){
      axios.get("http://localhost:5000/users/converstion",{rname: this.name, sname: this.inConversationWith })
        .then(res=>{
            if(res.data.msg){
                this.userData = res.data.docs;
            }
        })
        .catch(err => alert(err));
  },
  methods:{
      whosend(value){
          if (value==this.name){
              return false;
          }
          else{
              return true;
          }
      },
      sendmessage(msg){
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
      }
    }
    
}
</script>
<style scoped>
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
</style>