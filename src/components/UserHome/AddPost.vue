<template>
<div>
                
    <div class="writepost" >
         <div id="writepost1">
                                
            <form @submit="addPost" id="form1" >
                    
                         <img src="../../../images/ProfilePic.jpg" id="profileicon">   
                        <textarea style="font-size:15px; width:75%; vertical-align:middle; margin:10px;"  rows="3" v-model="postdata" placeholder="Write something here..."></textarea>
                        <button type="submit" style="margin-top:10px" class="btn btn-success"> + </button>
                 
                 
            </form>
         </div>
    </div>
         


            <!-- yaha chai get posts aaune thau -->
            
       <div id ="postmain" >
           
            <div class="postfeed" v-for="(item,index) in posts " :key="index">
               
                
                <!-- Yo chai post ko content-->
                
                    
                    <div class="toppost">
                        <table id="posttable">
                                <tr>
                                <td rowspan="2" style="width:80px"><img src="../../../images/ProfilePic.jpg"  id="posticon"></td>     
                                <td style="font-size: 20px; color:forestgreen; font-weight:bold" >{{item.name}}</td>
                            </tr>
                            <tr>
                                
                                <td style="color: grey">{{`${dateformat(item.date)}`}}</td>
                            </tr>
                        </table>
                    </div>
                
                
                    <div class="postarea">       
                        <div class="postcontent">
                            <b style="font-size: 15px">{{item.content}}</b>
                        </div>
                    </div>
                
               
            <div class="changestat">
                <table id="statstable">
                    <tr>
                        <td>
                            <button id="btnstats" class="btn btn-success" @click="addLiked(item.like,posts.indexOf(item))" v-if="(item.like)" style="background-color: green;color: white;"><i class="fas fa-thumbs-up"></i></button>
                            <button id="btnstats" class="btn btn-success" @click="addLiked(item.like,posts.indexOf(item))" v-else style="background-color: white;color: green;"><i class="fas fa-thumbs-up"></i></button>                                                                     
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
                                
                                
      
     
        
    
</template>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>


import jwtDecode from 'jwt-decode'
import axios from 'axios'
import moment from 'moment'


export default {
    
    name: "AddPost",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            postdata: '',
            name : decode.name,
            posts:[],
            error: '',
            formatedate:''
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
    methods: {
        dateformat(value){
            if (value) {
                return moment(String(value)).format('hh:mm MM/DD/YYYY')
            }
        },
        addPost(){
            axios.post('http://localhost:5000/users/post',{post: this.postdata,username: this.name})
                
                .then(res=>{
                    if(res.data.msg){
                        alert("Posted")
                        
                    //gettin all the post including the new one
                        axios.get("http://localhost:5000/users/post")
                    
                            .then(res=>{
                                if(res.data.msg){
                                    
                                    this.posts = res.data.docs;
                                    
                                }
                            })
                            .catch(err =>alert(err));  
                    }
                })
                .catch(err => alert(err));
            this.postdata= " ";

        }
    }
    
}
</script>

<style scoped>

.writepost{
    padding-top: 10px;
    padding-left: 20px;
    width: 100%;
    background-color: white;
    
}
#writepost1{
    padding: 4px;
}


#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    
    vertical-align:middle;
    border: 5px solid rgb(146, 209, 150);
   
   
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
    
 }
 .postfeed{
    margin-top:3px;
    padding-top:5px;
   
    width: 100%;
    color: black;
    background-color: white;
    border: 1px solid lightgray;
    
   
   
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
    margin-left: 80px;
    margin-top:10px;
    margin-bottom: 10px;
    word-wrap: break-word;
    text-align: left;
    font-size: 12px;
    color:black;
    background-color: rgb(197, 255, 197);
    padding: 10px;
    border-radius: 20px;
    
}
.postarea{
    border-bottom: 1px solid grey;
    padding-left: 10px;
    padding-right: 10px;
}

#btnstats{
    
     font-weight: 700; 
     
     width:150px;
}
.changestat{
    padding-top:10px;
   padding-bottom:10px;
   margin-left: 40px;
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
    padding:3px; 
    }
@media only screen and (max-width: 1200px) {
    textarea{
        width: 70%;
    }
}  



    
</style>
