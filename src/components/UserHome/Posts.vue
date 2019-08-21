<template>
    <div> 
       <div id ="postmain" class="container">
           
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
                                
                                <td style="color: grey">{{item.date.getDate()}}</td>
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
                <div class="container">
            <div class="changestat">
                <table id="statstable">
                    <tr>
                        <td>
                            <button id="btnstats" class="btn btn-success" @click="addLiked(item.liked,data1.indexOf(item))" v-if="(item.liked)" style="background-color: green;color: white;"><i class="fas fa-thumbs-up"></i></button>
                            <button id="btnstats" class="btn btn-success" @click="addLiked(item.liked,data1.indexOf(item))" v-else style="background-color: white;color: green;"><i class="fas fa-thumbs-up"></i></button>                                                                     
                        </td>
                        <td>
                            <button id="btnstats"   class="btn btn-success" @click="(item.commentshow=!item.commentshow)" v-bind:value="item.commentshow" v-if="(item.commentshow)" style="background-color: green; color: white"><i  class="fas fa-comment-dots"></i></button>
                            <button id="btnstats" class="btn btn-success" @click="(item.commentshow=!item.commentshow)" v-bind:value="item.commentshow" v-else style="background-color: white; color: green"><i class="fas fa-comment-dots"></i></button>                                              
                        </td>                                                          
                    </tr>
                </table>
                <div  v-if ="(item.commentshow)">
                    <input type="text" style="width: 80%"  v-model="item.commenting"><button id="btn" class="btn btn-success" @click="addComment(item.commenting,data1.indexOf(item))" >Comment </button>
                    <div style="max-height:30%; overflow-y:scroll;">
                        <div v-for = "(comment,index) in item.comments " :key="index">
                            <table>
                                <tr>
                                    <td width=10px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                    <td>
                                        <div class="postcontent" >
                                            {{comment.comment_content}} 
                                        </div>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
       </div>
    </div>
</template>
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
import axios from 'axios';
export default {
    name: "Posts",
    methods:{
                  addItem:function(product){
                    this.data1.push({ id:this.data1.length, name:this.username, post: product , date: date, comments:[], liked:false})
                   // alert("Posting Successful");
                  },
                  addComment:function(commenting,index){
                    
                    var ins = this.data1[index];
                    ins.comments.push({name:this.username, comment_content:commenting,date: date})
                  },
                  addLiked:function(liking,index){
                    var lik = this.data1[index];
                    lik.liked=!lik.liked;
                  }
                  
                },
    data(){
      return{
        posts:[
        ],
        error: ''

      }
    },
    created(){
      
        axios.get("http://localhost:5000/users/post")
        
        .then(res=>{
          if(res.data.msg){
            //alert("post request pathayo")
            this.posts = res.data.docs;
            
          }
        })
        .catch(err =>alert(err));  
    },
    
}
</script>

<style scoped>
.newsfeed{
    margin-top: 10px;
   
    width: 100%;
    color: black;
    background-color: white;
    border-radius: 20px;
    
   
}
.followerinfo{
    background-color: white;
    width: 100%;
  
    border-radius: 20px;
    
}
#tables3{
    
    width: 100%;
    color: black;
    border-collapse: collapse;
    
    
}
#tables3 tr:nth-child(2) {
    border-bottom: thin solid;
}



  #tables3 th,#tables3 td {
    padding: 5px;
   
    font-size: 15px;
   
  }
  #otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   vertical-align:top  ;
   border: 3px solid darkgrey;
 
}

#tables3 input[type=text]{
    width: 70%;
    padding: 5px;
    margin: 1%;
    }
 #commentsection{
    padding: 10px;
    background-color: lightgrey;
    border-radius: 20px;
    width: 70%;
}
#posttable{
     
     width:40%;
     margin-left: 20px;
     margin-bottom: 20px;   
 }
 .postfeed{
    padding-top: 10px;
    margin-top:20px;

   
    width: 100%;
    color: black;
    background-color: white;
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
#postmain{
  background-color:rgb(214, 240, 214);
  padding-top:5px;
  padding-bottom: 5px;
}
  
</style>
