<template>
    <div>
        <h2> UserBio goes here</h2>
        <!-- Yo unserlined part ma chai info hala hai -->
        <p> Full name: ________</p>
        <p> Contact : ________</p>
        <p> Address : ________</p>
        <p> Bio : ________</p>

    </div>
</template>
<script>
import axios from 'axios'
import jwtDecode from 'jwt-decode'
export default {
    name: "UPBio",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            username:decode.name,
            userData: []
        }
    },
    created(){
        axios.get(`http://localhost:5000/users/info/${this.username}`)
        .then(res =>{
            if(res.data.success){
                
                this.userData = res.data.docs;
              /*
                dhoju yaha user data ma chai yo component created hune bitikai k k 
                database ma cha user ko aaucah ani timile cahi 
                suru ma yo account page suru hune bitikai db ma bhako inf dekhau hai 
                 
                 */
                
            }
        })
        .catch(err=> alert(err));
    }

}
</script>
<style scoped>
    
</style>