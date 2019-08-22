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
                        Timeline

                            <div id ="postmain" class="container">
                                
                                    <div class="postfeed" v-for="(item,index) in posts " :key="index">
                                    
                                        
                                        <!-- Yo chai post ko content-->
                                        <div class="container">
                                            
                                            <div class="toppost">
                                                <table id="posttable">
                                                        <tr>
                                                        <td rowspan="2"><img src="../../../../images/ProfilePic.jpg"  id="posticon"></td>     
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

                                        </div>
                                    </div>
                            
                        
                        


                    </div>
                    <div class="tab-pane fade" id="follower" role="tabpanel" aria-labelledby="follower-tab">
                        Followers
                      
                        <div class="followtext">
                        <div id="followtext1">
                           
                           <ul class="list-group list-group-flush" v-for="(item,index) in followers" :key="index">
                  
                            <li class="list-group-item"><img src="../../../../images/ProfilePic.jpg" id="otherprofileicon" >{{item.name}}
                            
                            </li>
              
                 
                 
                          </ul>

                    </div>
                </div>

                    </div>
                    <div class="tab-pane fade" id="following" role="tabpanel" aria-labelledby="following-tab">
                        following
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
        //const uname = this.name;
        
        axios.get(`http://localhost:5000/users/profile/post/${this.name}`)
        
        .then(res=>{
          if(res.data.msg){
            alert("post request pathayo")
           
            this.posts = res.data.docs;
            
          }
        })
        .catch(err =>alert(err)); 
        
        //followers ko lagi
        axios.get(`http://localhost:5000/users/follow/${this.name}`)
        
        .then(res =>{
            const data = res.data.docs;
            alert(data.followedBy)
            this.followers = data.followedBy;
        })
        .catch(err=> alert(err))


        //following ko lagi 
        // axios.get("http://localhost:5000/users/")
        //     .then(res =>{
        //         this.
        //     })
    },
    methods:{
                  
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