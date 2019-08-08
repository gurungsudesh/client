<template>
     
       
        
<div id="Signin">
    <form @submit="login">
        <input type="text"  v-model="username" id="username" placeholder="Username">
        <input type="password"  v-model="password" id="password" placeholder="Password">
        <!--<input type="submit" name="submit" value="Sign Up!">-->
        <button type="submit" class="btn btn-success">Login</button>
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
    right: 20px;  
}
input[type=text], input[type=password]{
    
    border: 1px solid black;
border-radius: 10px;
margin: 10px;
right: 0%;
}

button[type="submit"] {
    
    font-size: 15px;
    font-weight: bold;
    padding: 5px;
    padding-right: 10px;
    padding-left: 10px;
    border-radius: 10px;
    
    border: none;
    
   
}
#login_text{
color:white;
text-decoration:none;
}
</style>
