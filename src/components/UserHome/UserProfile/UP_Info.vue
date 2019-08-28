<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-auto">
                    <img src="../../../../images/ProfilePic.jpg" >
                </div>
                <div class="col-md-auto">
                    <h3>{{name}}</h3>
                        <p class="text-left" style="color: gray; font-size: 12px" >Made at janaury 2016 
                            <br>
                            <!-- Yaha 99 bhako thau ma chai aauna paryo -->
                            99 followers<br>
                            99 following<br>
                            
                        </p>
                        <button id="btn" class="btn btn-success" >Edit Profile</button>
                </div>
            </div> 
        </div>
    </div>
</template>
<script>
import axois from 'axios';
import jwtDecode from 'jwt-decode'
export default {
    name: "UPInfo",
     data(){
         
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            name : decode.name,
            followers: '',
            following: ''
        }
    },
    created(){

        // yaha chai followers ra follow haru aaune gar hai 

       // axios.get(`http://localhost:5000/${this.name}`)

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