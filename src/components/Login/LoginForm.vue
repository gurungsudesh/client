<template>
     
       
        
<div id="Signin">
    
        <input type="text"  v-model="username" size="25" placeholder="Username">
        <input type="text" v-model="password" name="password" size="25" placeholder="Password">
        <!--<input type="submit" name="submit" value="Sign Up!">-->
        <button type="submit" v-on:cick="login" ><router-link id="login_text" to="/about">Login</router-link></button>
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
    padding-top: 50px;
    padding-left: 50px;
}
input[type="text"]{
    background-color: white;
    
    margin-right: 40px;
    border: 1px solid black;
    padding: 5px;
    outline:none;
    border-radius: 10px;
}


button[type="submit"] {
    background-color: rgb(56, 0, 0);
    font-size: 15px;
    font-weight: bold;
    padding: 5px;
    padding-right: 10px;
    padding-left: 10px;
    border-radius: 10px;
    
    border: none;
    
    margin-left: 10px;
}
#login_text{
color:white;
text-decoration:none;
}
</style>
