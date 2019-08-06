<template>
     
       
        
<div id="Signin">
    
        <input type="text"  v-model="username" id="inputEmail3" placeholder="Username">
        <input type="password"  v-model="password" id="inputPassword3" placeholder="Password">
        <!--<input type="submit" name="submit" value="Sign Up!">-->
        <button type="submit" class="btn btn-success" v-on:cick="login" ><router-link id="login_text" to="/about">Login</router-link></button>
        <p class="error" v-if="error">{{error}}</p>
                       
</div>
               
        
        
        
        
        
        
  
</template>

<script>
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
        async login(){
           // const {title, completed} = newTodo;
            axios.post('http://localhost:5000/login', {username,password})
                .then(res => 
                    function(data) {
                        console.log(data);
                        if (data.success) {
                            var storage = window.localStorage;
                            var token = data.token;
                            storage.setItem('token', token)
                            storage.setItem('username', username)
                            this.$router.push('About')
                            //window.location.href = "http://localhost:3000/auth/home";
                            // $.get("http://localhost:5000/auth/home");
                            // Login successful 
                        } else {
                            // Login Failed
                            errorMessage = $("#errorMessage").text(data.message)
                        }
                        
                    }
                
                )
                .catch(er => console.log(err));
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
