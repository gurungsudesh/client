<template>
    <div>
        <div class="formmain"  >
            <form @submit="onSubmit" autocomplete="off">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item" > 
                    <input type="text" class="form-control"  v-model="username" id="inputEmail3" placeholder="Username" required>
                    <span id="errorshow" style="color:red; font-size:12px;" v-if='msg.username'>{{msg.username}}</span>
                    </li>
                    

                
                    <li class="list-group-item">
                    <input type="text" class="form-control" v-model="email" id="inputEmail3" placeholder="Email" required>
                    <span id="errorshow" style="color:red; font-size:12px;" v-if='msg.email'>{{msg.email}}</span>
                    </li>
                    
                

                
                    <li class="list-group-item">
                        <input type="password" class="form-control" v-model="password" id="inputPassword3" placeholder="Password" required>
                        <span  id="errorshow" style="color:red; font-size:12px;" v-if='msg.password'>{{msg.password}}</span>
                    </li>

                
                    <li class="list-group-item">
                    <input type="password" class="form-control" v-model="confpass" id="inputPassword3" placeholder="Confirm Password" required>
                     <span id="errorshow" style="color:red; font-size:12px;" v-if='msg.confpass'>{{msg.confpass}}</span>
                    </li> 
                    <!--  Yo chai error aaune registration aauda -->
                    <p style="color:red ; font-weight:none; font-size: 15px; left:10%; bottom:15%; z-index: +1; position: absolute;" class="err" v-if="error"> {{error}}</p>
               

                 <li class="list-group-item" > 
                <button type="submit" class="btn btn-success" ><!--<router-link to="/about">Sign Up</router-link>--> Sign Up</button> 
                </li>
                <li class="list-group-item"> 
                    <router-link style="color:green ; font-weight:none; font-size: 12px;" to="/">You have an account?</router-link>
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
#errorshow{
    
   z-index: +1;
   position: absolute;
   border: 1px solid rgb(255, 111, 111);
   left:200px;
   bottom: 0px;
   background-color: white;
   padding: 5px;
   border-radius: 5px;
}
.btnform{
    width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
</style>
