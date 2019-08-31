<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-auto">
                    <img src="../../../../images/ProfilePic.jpg" >
                </div>
                <div class="col-md-auto">
                    <h3>{{name}}</h3>
                        <p class="text-left" style="color: gray; font-size: 12px" > 
                            Made at
                            <br>
                            
                            <!-- Yaha 99 bhako thau ma chai aauna paryo -->
                            {{followersNum}} followers<br>
                            {{followingNum}} following<br>
                            
                        </p>
                        <button id="btn" class="btn btn-success" >Edit Profile</button>
                </div>
            </div> 
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import jwtDecode from 'jwt-decode'
export default {
    name: "UPInfo",
     data(){
         
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            name : decode.name,
            followersNum: '',
            followingNum: '',
            date: ''
        }
    },
    created(){

        // yaha chai followers ra follow haru aaune gar hai 

       //followers ko lagi 
       axios.get(`http://localhost:5000/users/follower/${this.name}`)
        .then(res =>{
            if(res.data.msg){
                const followers = res.data.docs;
                this.followersNum = followers.length;
            }
            
        })
        .catch(err=> alert(err));
        //following ko lagi 
        axios.get(`http://localhost:5000/users/follow/${this.name}`)
            .then(res =>{
                if(res.data.msg){
                    const following = res.data.docs;
                    this.followingNum = following.length;
                }
            })
            .catch(err=> alert(err));


        //date laune 
        axios.get(`http://localhost:5000/users/user/${this.name}`)
            .then(res =>{
            
                this.date = res.data.docs;
            })
            .catch(err => alert(err))

    }
}
</script>
<style scoped>
    #btn{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
     
}
img{
    width: 100px;
    height: 100px;
    border-radius: 50%;
    border: 10px solid rgb(158, 221, 158);

}
#btn:active{
    background-color: green;
    color: white;
}
</style>