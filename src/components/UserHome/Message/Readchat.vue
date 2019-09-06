<template>
    <div>
        <div class="topright">
                    <table>
                        <tr>
                            <td style="width: 20%">
                                    <img src="../../../../images/ProfilePic.jpg">
                            </td>
                            <td style="width: 80%; text-align: left">
                                    <span style="margin-left: 50px">commment hunxa yaha</span>
                            </td>
                            <td style="width: 20%">

                            </td>
                        </tr>
                        <tr>
                            <td style="width: 20%">
                                    
                            </td>
                            <td style="width: 80%; text-align: right">
                                    <span style="margin-left: 50px">commment hunxa yaha</span>
                            </td>
                            <td style="width: 20%">
                                    <img src="../../../../images/ProfilePic.jpg">
                            </td>
                        </tr>
                    </table>
                    
                </div>
                <div class="bottomright">
                        <form class="form-inline" id="formmessage">
                                <input class="form-control" type="text" id="sendm" placeholder="message..">
                                <button id="mbtn" class="btn btn-success" type="submit"><i class="fas fa-search" ></i></button>
                        </form>
                </div>
            
    </div>
</template>
<script>
export default {
    name: "Readchat",
    data(){
    return {
       
        
    }
  },
  methods:{
      }
    
}
</script>
<style scoped>
    .topright{
        position: absolute;
        top:0px;
        width: 100%;
        height:90%;
        background-color: blueviolet;
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
        position: absolute;
        top:90%;
        width: 100%;
        height: 10%;
        background-color: blue;
    }
    .topright img{
            border-radius: 50%;
            width: 50px;
            height: 50px;
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
</style>