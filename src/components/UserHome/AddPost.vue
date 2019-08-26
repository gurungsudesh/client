<template>
                
         <div class="writepost" >
         <div id="writepost1">
                                
            <form @submit="addPost" id="form1" >
                    
                         <img src="../../../images/ProfilePic.jpg" id="profileicon">   
                        <textarea style="font-size:15px; width:75%; vertical-align:middle; margin:10px;"  rows="3" v-model="postdata" placeholder="Write something here..."></textarea>
                        <button type="submit" style="margin-top:10px" class="btn btn-success"> + </button>
                 
                 
            </form>
                                
                                
      </div>
     </div>
        
    
</template>

<script>

import jwtDecode from 'jwt-decode'
import axios from 'axios'

export default {
    name: "AddPost",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            postdata: '',
            name : decode.name
        }
    },
    methods: {
        addPost(){
            axios.post('http://localhost:5000/users/post',{post: this.postdata,username: this.name})
                
                .then(res=>{
                    if(res.data.msg){
                        alert('Posted')
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
    margin-top: 10px;
    padding-left: 20px;
    width: 100%;
    
    
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
@media only screen and (max-width: 1200px) {
    textarea{
        width: 70%;
    }
}    
</style>
