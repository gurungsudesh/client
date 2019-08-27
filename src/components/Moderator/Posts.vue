<template>
    <div>
        <div class="container">
           
            <div class="postfeed" v-for="(item,index) in posts " :key="index">
               
                
                <!-- Yo chai post ko content-->
                <div class="container">
                    
                    <div class="toppost">
                        <table id="posttable">
                                <tr>
                                <td rowspan="2"><img src="../../../images/ProfilePic.jpg"  id="posticon"></td>     
                                <td style="font-size: 15px; color:forestgreen; font-weight:bold" >{{item.name}}</td>
                            </tr>
                            <tr>
                                
                                <td style="color: grey">{{item.date}}</td>
                            </tr>
                        </table>
                    </div>
                </div>
                <div class="container">
                    <div class="postarea">       
                        <div class="postcontent">
                            <b style="font-size: 13px">{{item.content}}</b>
                        </div>
                    </div>
                </div>
            

             <!-- Yo chai like, comment aaune thau-->

                <div class="container">
                    <div class="changestat">
                        <table id="statstable">
                            <tr>
                                <td>
                                <button id="dbtn" class="btn btn-success"  @click="deletePost(item._id)">Delete</button>
                                </td>
                            </tr>

                        </table>
                    </div>
                </div>      





            </div>
        </div>
                
    </div>
</template>

<script>



import axios from 'axios'
export default {
    name: "Posts",
    data(){
        return{
            posts: []
        }
    },
    created(){
        
        axios.get("http://localhost:5000/moderator/post")
            .then(res=>{
                if(res.data.msg){
                    this.posts = res.data.docs;
                }
            })
            .catch(err => alert(err))
    },
    methods: {
        deletePost(ID){
            axios.delete(`http://localhost:5000/moderator/post/${ID}`)
                .then(res =>{
                    if(res.data.deleted){
                        //deleted
                        alert("deleted")
                        
                }
            })

            .catch(err => alert(err));

            axios.get("http://localhost:5000/moderator/post")
            .then(res=>{
                if(res.data.msg){
                    this.posts = res.data.docs;
                }
            })
            .catch(err => alert(err));

            
        }
    }
}
</script>
<style scoped>


#posttable{
     
     width:40%;
     margin-left: 20px;
     margin-bottom: 20px;   
 }
 .postfeed{
    margin-top: 10px;
   
    width: 50%;
    color: black;
    background-color: burlywood;
    border-radius: 20px;
    border-bottom: 4px solid gray;
   
}
#posticon{  
    border-radius: 50%;
    width: 60px;
    height: 60px;
    margin-right: 10px;
    vertical-align:top  ;
    border: 7px solid rgb(157, 255, 173);
  
}
.postcontent{
    margin-top:10px;
    margin-bottom: 10px;
    word-wrap: break-word;
    text-align: left;
    font-size: 12px;
    color:black;
    background-color: rgb(152, 255, 152);
    padding: 10px;
    border-radius: 20px;
    
}
.postarea{
    border-bottom: 2px solid grey;  
}
.toppost{
    border-bottom: 2px solid grey;
}
#btnstats{
    
     font-weight: 700; 
     
     width:150px;
}
.changestat{
    padding-top:10px;
   padding-bottom:10px;
}
#statstable td{
    padding-left:50px;
}
#btn{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:80px;
     
}
#dbtn{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
     float:right;
}
#dbtn:active{
    background-color: green;
    color: white;
}
</style>

