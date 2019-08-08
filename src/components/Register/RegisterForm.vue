<template>
    <div>
        <div class="formmain">
            <form @submit="onSubmit">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item"> 
                    <input type="text" class="form-control" v-model="username" id="inputEmail3" placeholder="Username" required>
                    </li>
                    <span style="color:red" v-if='msg.username'>{{msg.username}}</span>

                
                    <li class="list-group-item">
                    <input type="email" class="form-control" v-model="email" id="inputEmail3" placeholder="Email" required>
                    </li>
                    <span style="color:red" v-if='msg.email'>{{msg.email}}</span>
                

                
                    <li class="list-group-item">
                    <input type="password" class="form-control" v-model="password" id="inputPassword3" placeholder="Password" required>
                </li>
                <span style="color:red" v-if='msg.password'>{{msg.password}}</span>
                

                
                    <li class="list-group-item">
                    <input type="password" class="form-control" v-model="confpass" id="inputPassword3" placeholder="Confirm Password" required>
                </li>
                <span style="color:red" v-if='msg.confpass'>{{msg.confpass}}</span>
                

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
            error: '',
            msg: [],
            errmsg: []
        }
    },
    watch:{
        username(value){
            this.username = value,
            this.check_username(value)
        },
        email(value){
            this.email = value,
            this.check_email(value);
        },
        password(value){
            this.password = value,
            this.checkPassword(value);
        },
        confpass(value){
            this.confpass = value,
            this.checkConfirmPassword(value);
        }
    },
    methods: {
        check_username(value){
            if(value.length<6){
                this.msg['username'] = 'Username must be atleast contain 6 characters'
            }
            else{
                this.msg['username'] = ''
            }
        },
        check_email(value){
            if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(value))
                {
                      this.msg['email'] = '';
                }
                else{
                    this.msg['email'] = 'Please type correct email'
                }
        },
        checkPassword(value){
            if(value.length<6){
                this.msg['password'] = 'Password must contain atleast  6 characters'
            }else{
                this.msg['password'] = ''
            }
        },
        checkConfirmPassword(value){
            if(value == this.password){
                this.msg['confpass'] = ''
            }else{
                this.msg['confpass'] = 'Password and confirm password do not match'
            }
        },
        // onSubmit(username,email,password){
        //     if(this.username =='' || this.email =='' || this.password =='' || this.confpass ==''){
        //         if(this.username ==''){
        //             this.errmsg['username'] = 'Username field is required'
        //         }
        //     }
        // },
        onSubmit(e){
            e.preventDefault();

            axios.post('http://localhost:5000/users/register', { username: this.username, email: this.email, password: this.password})
                .then(res => {
                    
                        if (res.data.success) {
                            this.error = res.data.msg;
                        } else {
                            // Login Failed
                            this.error = res.data.msg;
                        }
                    }
                )
                .catch(err => this.error = err);
        }
    }
}
</script>

<style scoped>
.formmain{
    position: relative;
    margin-bottom: 5%;
    transform: scale(0.9, 0.9);
    
 
}
a{
    text-decoration: none;
    color:white;
    font-weight: bold;
}
</style>
