<template>
    <div id = "pok"> 
       <div class="newsfeed" v-for="(item,index) in data1 " :key="index">
              <div class="followerinfo" >                                    
                <table id="tables3">
                              <tr >
                                <td  rowspan="3" width=20px valign="top"><img src="bullet.jpg"  id="otherprofileicon"></td>
                                <td colspan="2" align="left" style="font-size: 20px; font-weight: bold ; padding-top:15px ;" >{{item.name}}</td>
                              </tr>
                              <tr>
                                <td colspan="2" style="text-align: left">
                                  {{ item.post }}</td> 
                              </tr>
                              <tr >
                                 
                                  <td><button  type="button" style="margin-right: 5px" @click="addLiked(item.liked,data1.indexOf(item))"><div v-if="(item.liked)" style="color: red">Like</div><div v-else style="color: black">Like</div> </button>
                                  Comment: <input type="text"  v-model="item.commenting"><button type="button" @click="addComment(item.commenting,data1.indexOf(item))" >Comment</button> </td> 
                                </tr>
                            
                            </table>
                            
                              <div v-for = "(comment,index) in item.comments " :key="index">
                            <table id="tables3" >
                                <tr>
                                  <td width=10px><img src="bullet.jpg" align="left" id="otherprofileicon"></td>
                                  <td><div id="commentsection" >
                                     {{comment.comment_content}} 
                                  </div></td>
                                </tr>
                              </table>
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
    data(){
      return{
        data1:[
        ],
        error: ''

      }
    },
    created(){
      
        axois.get("http://localhost:5000/users/post")
        alert("post request pathayo")
        .then(res=>{
          if(res.data.msg){
            this.data1 = res.data.docs;
            alert(this.data1)
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
  
</style>
