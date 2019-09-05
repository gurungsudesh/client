<template>
    <div> 
         <div class="hottopic">
           
            <div id="hotcontent">
               <ul class="list-group list-group-flush">
                  <li class="list-group-item"> <h4><b>Hot topics</b></h4> </li>
                  <li class="list-group-item">Topics 2</li>
                 <li class="list-group-item">Topics 3</li>
                 <li class="list-group-item">Topics 4</li>
                 <li class="list-group-item">Topics 5</li>
                  <li class="list-group-item">Topics 6</li>
            </ul>
                        </div>
                        </div>
                        
                
               
    </div>
</template>

<script>
import axios from 'axios'
// import jwtDecode from 'jwt-decode'
export default {
    name: "HotTopics",
    data(){
      // const token = localStorage.usertoken
      // const decode = jwtDecode(token)
      return{
        name: this.name,
        total: [],
        posts: []
      }
    },
    created(){


      //This is still construction
  //----------------------------------------------------------------------

      // All posts liyo
      axios.get("http://localhost:5000/users/post")
        .then(res=>{
          if(res.data.docs){
            this.posts = res.data.docs;
            //get likes for post id
          
            for(var i=0; i<this.posts.length; i++){
              
              axios.get(`http://localhost:5000/users/post/likes/${this.posts[i]._id}`)
                .then(res=>{
                  if(res.data.docs != ''){
                    this.total[i] = res.data.docs;
                    
                  }else{
                    //err
                  }
                })
                .catch(err => alert(err));
            }
          }
        })
        .catch(err=> alert(err));

       //----------------------------------------------------------------------
    }
}
</script>

<style scoped>

  .hottopic{
    border: 1px solid lightgrey;
      margin: 20px;
    
      width: 80%;
    background-color: rgb(245, 253, 236);
       
      
    
  }
  ul{
    border-radius: 10px;
  }
  li{
    background-color: rgb(245, 253, 236);
    border-radius: 10px;
  }
  #hotcontent{
      font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    font-size:15px;
    padding:5%;
  
   color: black;
    
  }
 
</style>
