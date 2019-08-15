<template>
    <div class="container">             
         <div class="writepost" >
         <div id="writepost1">
                                
            <form @submit="addPost" id="form1" >

                  <div class="form-row">
                    <div class="form-group col-md-1.5">
                         <img src="../../../images/ProfilePic.jpg" id="profileicon">   
                    </div>
                    <div class="form-group col-md-9">          
                  <div class="form-group shadow-textarea">
                     <textarea class="form-control z-depth-1" style="font-size:15px" id="exampleFormControlTextarea6" rows="3" v-model="postdata" placeholder="Write something here..."></textarea>
                    </div>
                 </div>
              <div class="form-group col-md-1">
                <button type="submit" style="margin-top:10px" class="btn btn-success"  >Post</button>
                 </div>
                 </div>
            </form>
                                
                                
      </div>
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
.container{
    border-bottom: 10px solid lightgrey;
}
.writepost{
    margin-top: 10px;
    width: 100%;
   
    
    
}
#writepost1{
    padding: 4px;
}

#Imageinserticon{
   margin-right: 10px;
    margin-left: 10px;
    vertical-align:bottom;
    padding-bottom: 5px;
    border: 2px solid rgb(146, 209, 150);
   
}
#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-right: 10px;
    vertical-align:middle;
    border: 5px solid rgb(146, 209, 150);
   
   
}
</style>
