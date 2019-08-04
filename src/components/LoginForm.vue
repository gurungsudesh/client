<template>
     
       
        
             <div id="Signin">
                            
                    <input type="text"  name="Email" size="25" placeholder="Email Address">
                    <input type="text"  name="password" size="25" placeholder="Password">
                    <!--<input type="submit" name="submit" value="Sign Up!">-->
                    <button type="submit" ><router-link id="login_text" to="/about">Login</router-link></button>
              </div>
               
        
        
        
        
        
        
  
</template>

<script>
export default {
    name: "LoginForm"
  
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
