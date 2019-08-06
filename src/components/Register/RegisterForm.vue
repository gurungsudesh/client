<template>
    <div>
        <div class="formmain">
        <form @submit="onSubmit">
            <ul class="list-group list-group-flush">
              <li class="list-group-item"> 
            <input type="text" class="form-control" v-model="username" id="inputEmail3" placeholder="Username"></li>
              <li class="list-group-item">
                   <input type="email" class="form-control" v-model="email" id="inputEmail3" placeholder="Email">
              </li>
             <li class="list-group-item">
                  <input type="password" class="form-control" v-model="password" id="inputPassword3" placeholder="Password">
             </li>
             <li class="list-group-item">
                  <input type="password" class="form-control" v-model="confpass" id="inputPassword3" placeholder="Confirm Password">
             </li>
             <li> 
                 <!--  Yo chai error aaune registration aauda -->
                 <p style="color:red ; font-weight:none; font-size: 15px;" class="err" v-if="error"> {{error}}</p>
             </li>
           <li class="list-group-item"> 
               <button type="submit" class="btn btn-success" ><!--<router-link to="/about">Sign Up</router-link>--> Sign Up</button> 
           </li>
           <li class="list-group-item"> 
                 <router-link style="color:green ; font-weight:none; font-size: 15px;" to="/">You have an account?</router-link>
           </li>
            </ul>

       
       
         </form>
        </div>
    
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: "RegisterForm",
    data(){
        return{
            username: '',
            email: '',
            password: '',
            confpass: '',
            error: ''
        }
    },
    methods: {
        onSubmit(username,email,password){

            // client side validation


            axios.post('http://localhost:5000/register', {username,email,password})
                .then(res => function (data) {
                        if (data.status) {
                            this.err = data.status;
                        } else {
                            // Login Failed
                            this.err = data.status;
                        }
                        
                    }
                )
                .catch(err => this.error =err.message);
        }
    }
}
</script>

<style scoped>
.formmain{
    position: relative;
   
    width: 100%;
}
a{
    text-decoration: none;
    color:white;
    font-weight: bold;
}
</style>
