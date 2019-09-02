<template>
    <div>
        
        <div  id ="tabs">
            <ul class="nav nav-tabs justify-content-center"  id="myTab" role="tablist">
                    <li class="nav-item">
                        <a class="nav-link active" id="home-tab" data-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true">Timeline</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" id="follower-tab" data-toggle="tab" href="#follower" role="tab" aria-controls="follower" aria-selected="false">Followers</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link" id="following-tab" data-toggle="tab" href="#following" role="tab" aria-controls="following" aria-selected="false">Following</a>
                    </li>
            </ul>
                    <div class="tab-content" id="myTabContent">
                    <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">
                        

                            <div id ="postmain">
                                
                                    <div class="postfeed" v-for="(item,index) in posts " :key="index">
                                    
                                        
                                        <!-- Yo chai post ko content-->
                                       
                                            
                                            <div class="toppost">
                                                <table id="posttable" >
                                                        <tr>
                                                        <td rowspan="2" style="width:40px"><img src="../../../../images/ProfilePic.jpg"  id="posticon"></td>     
                                                        <td style="font-size: 15px; color:forestgreen; font-weight:bold" >{{item.name}}</td>
                                                    </tr>
                                                    <tr>
                                                        
                                                        <td style="color: grey">{{item.date}}</td>
                                                    </tr>
                                                </table>
                                            </div>
                                       
                                        
                                            <div class="postarea">       
                                                <div class="postcontent">
                                                    <b style="font-size: 13px">{{item.content}}</b>
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
                    <div class="tab-pane fade" id="follower" role="tabpanel" aria-labelledby="follower-tab">
                        
                      
                        <div class="followtext">
                        <div id="followtext1">
                           
                           <ul class="list-group list-group-flush" v-for="(item,index) in followers" :key="index">
                  
                            <li class="list-group-item">
                                <form @submit="follow(name,id, item.name, item._id )">
                                <img src="../../../../images/ProfilePic.jpg" id="otherprofileicon" >
                                <router-link :to="{name: 'otherprofile',params:{name: item.followedBy, status: 'Follow'}}" >{{item.followedBy}}</router-link>
                               <button type="submit" class="btn btn-success" id="followingbtn"><span>Following</span></button>
                               </form>
                            </li>
                            
              
                 
                 
                          </ul>

                    </div>
                </div>

                    </div>
                    <div class="tab-pane fade" id="following" role="tabpanel" aria-labelledby="following-tab">
                        
                        <div class="followtext">
                            <div id="followtext1">
                            
                                <ul class="list-group list-group-flush" v-for="(item,index) in following" :key="index">
                        
                                    <li class="list-group-item" >
                                     <form @submit="follow(name,id, item.name, item._id )">
                                         <img src="../../../../images/ProfilePic.jpg" id="otherprofileicon" >
                                         <router-link :to="{ name: 'otherprofile',params:{name: item.username, status: 'Unfollow'}}" >{{item.username}}</router-link>
                                         <button type="submit" class="btn btn-success" id="followbtn">Follow</button></form>
                                    </li>
                    
                        
                        
                                </ul>

                            </div>
                        </div>
                    </div>
                </div>
                
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import jwtDecode from 'jwt-decode'
export default {
    name: "UPTimeline",

    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            posts :[],
            followers: [],
            following: [],
            name : decode.name
        
        }
    },
    created(){
        const uname = this.name;
        
        axios.get(`http://localhost:5000/users/profile/post/${uname}`)
        
        .then(res=>{
          if(res.data.msg){

            this.posts = res.data.docs;
          }
        })
        .catch(err =>alert(err)); 
        
        //followers ko lagi
        axios.get(`http://localhost:5000/users/follower/${uname}`)
        .then(res =>{
            if(res.data.msg){
                this.followers = res.data.docs;
            }
        })
        .catch(err=> alert(err))


        //following ko lagi 
        axios.get(`http://localhost:5000/users/follow/${uname}`)
            .then(res =>{
                if(res.data.msg){
                this.following = res.data.docs;
                }
            })
            .catch(err=> alert(err));
            
    }
   
}
</script>
<style scoped>
    #tabs a{
        margin-top: 5%;
    color: green;
    font-size: 15px;
    font-weight: bold;
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
    
    padding-top:6px;
    border: 1px solid lightgray;
    width: 100%;
    color: black;
    background-color: white;
    
    
   
   
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
    background-color: rgb(157, 255, 173);
    padding: 10px;
    border-radius: 20px;
    width: 70%;
    
}
.postarea{
    border-bottom: 1px solid grey;
    padding-left: 10px;
    padding-right: 10px;
    width:100%;
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
    background-color: rgb(233, 233, 233);
    padding-left:2px;
    padding-right:2px; 
    padding-bottom:4px;
    
}
#followbtn{
    background-color: white;
    color: green;
    border-radius: 20px;
    font-weight: bold;
    border: 2px solid green;
    float: right;
}

#followingbtn{
    background-color: green;
    color: white;
    border-radius: 20px;
    font-weight: bold;
    border: 2px  solid green;
    float: right;
    width: 100px;
}
#followingbtn:hover span {display:none}
#followingbtn:hover:before {
    content:"Unfollow"
    }
#followingbtn:hover{
    background-color: white;
    color:green;
}
#followingbtn:active{
    background-color: green;
    color: white;
}
#followbtn:active{
    background-color: green;
    color: white;
}

  
</style>