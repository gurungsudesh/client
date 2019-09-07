<template>
    <div>
        <!-- tyo conversation ma click garyo vane get garcha message-->
        <div class="topright">
                    <table v-for="(item,index) in data1 " :key="index"   style="width:100%">
                    
                        <tr v-if="(whosend(item.sender))">
                            <td style="width: 10%">
                                    <img src="../../../../images/ProfilePic.jpg">
                            </td>
                            <td style="width: 80%; text-align: left">
                                    <span class="status" >{{item.message}}</span>
                            </td>
                            <td style="width: 10%">

                            </td>
                        </tr>
                        <tr v-else>
                            <td>
                                    
                            </td>
                            <td style="width: 80%; text-align: right">
                                    <span class="status" style="margin-left: 50px">{{item.message}}</span>
                            </td>
                            <td style="width: 10%">
                                    <img src="../../../../images/ProfilePic.jpg">
                            </td>
                        </tr>
                    
                    </table>
                    
                </div>
                <div class="bottomright">
                        <form class="form-inline" id="formmessage">
                                <input class="form-control" type="text" id="sendm" placeholder="message..">
                                <button id="mbtn" class="btn btn-success" type="submit">Send</button>
                        </form>
                </div>
            
    </div>
</template>
<script>
export default {
    name: "Readchat",
    data(){
    return {
        name:'Pokemon',
       data1 : [{
                    "id":0 ,
                    "sender":"Prashant Dhoju",
                    "receiver":"Pokemon",
                    "message":"asdasdasaPokemon",
                    
                },
                {   "id":1 ,
                    "sender":"Pokemon",
                    "receiver":"Prashant Dhoju",
                    "message":"saPokemon"
                },
                {    "id":2 ,
                    "sender":"Prashant Dhoju",
                    "receiver":"Pokemon",
                    "message":"saPokemon"
                }]
        
    }
  },
  methods:{
      whosend(value){
          if (value==this.name){
              return true;
          }
          else{
              return false;
          }
      }
      }
    
}
</script>
<style scoped>
    .topright{
        position: absolute;
        top:0px;
        width: 100%;
        height:90%;
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
        top:90%;
        width: 100%;
        height: 10%;
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
        border-radius: 30px;
        padding: 20px;
        width: 90%;
    }
    #formmessage{
        margin: 10px;
        
    }
    .status{
        background-color: lightgreen;
        padding: 10px;
        border-radius: 10px ;
    }
    td{
        padding: 5px;
    }
    button{

    }
    
</style>