<template>
    <div>
        <div class="formmain">
        <form>
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
           <li class="list-group-item"> 
               <button type="submit" class="btn btn-success"><router-link to="/about">Sign Up</router-link></button> 
           </li>
           <li class="list-group-item"> 
                 <router-link style="color:green ; font-weight:none; font-size: 15px;" to="/about">You have an account?</router-link>
           </li>
            </ul>

       
       
         </form>
        </div>
    
    </div>
</template>

<script>
export default {
    name: "RegisterForm"
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
