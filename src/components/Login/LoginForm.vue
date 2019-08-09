<template>
     
       
        
<div id="Signin">
    <form @submit="login">
        <ul style="font-size:13px">
        <li><input type="text"  v-model="username" id="username" placeholder="Username"></li>
        <li><input type="password"  v-model="password" id="password" placeholder="Password"></li>
        <!--<input type="submit" name="submit" value="Sign Up!">-->
        <li><button type="submit" class="btn btn-success">Login</button></li>
        </ul>
        <p class="error" v-if="error">{{error}}</p>
    </form>             
</div>
               
        
        
        
        
        
        
  
</template>

<script>
import axios from 'axios'
export default {
    name: "LoginForm",
    data(){
        return{
            username: '',
            password: '',
            error: ''
        }
    },
    methods: {
        login(){
            axios.post('http://localhost:5000/users/login', { username: this.username,password: this.password})
                .then(res => {
                        //alert(`Username: ${this.username}, Password: ${this.password}`)
                        if (res.data.success) {
                            // var storage = window.localStorage;
                            // var token = data.token;
                            // storage.setItem('token', token)
                            // storage.setItem('username', username)
                            this.$router.push('/about')
                            //window.location.href = "http://localhost:3000/auth/home";
                            // $.get("http://localhost:5000/auth/home");
                            // Login successful 
                        } else {
                            // Login Failed
                            this.error = res.data.msg;
                        }
                        
                    
                }
                   
                
                )
                .catch(err => this.err = err);
     }
    }



  
}

</script>

<style scoped>

 #Signin{
     position: absolute;
    padding-top: 50px;
    right:20px;  
}
input[type=text], input[type=password]{
    width: 40%;
  padding: 8px 20px;
  margin-right: 5px;
  
  display: inline-block;
  border: 1px solid lightgray;
  border-radius: 20px;
  box-sizing: border-box;
}
li{
    display: inline;
}

button[type="submit"] {
    position: absolute;
    font-size: 16px;
    font-weight: bold;
    width: 15%;
    
    border-radius: 20px;
    
    border: none;
    
   
}
#login_text{
color:white;
text-decoration:none;
}
input:focus{
    outline: none;
}
</style>
