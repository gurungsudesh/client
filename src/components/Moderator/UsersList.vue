<template>
    <div>
        
        <div id="followtext1">
            <ul class="list-group list-group-flush" v-for="(item,index) in allusers" :key="index" >
    
                <li class="list-group-item">
                
                    <img src="../../../images/ProfilePic.jpg" id="otherprofileicon" >
                    {{item.name}}                                        
                    
                    <button  @click ="deleteUser(item.name)" class="btn btn-success" id="followbtn">Delete</button>
                    
                
                </li>    
            </ul>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: "usersList",
    data(){
        return{
            allusers: []
        }
    },
    created(){
        //getting all the users 
        axios.get('http://localhost:5000/users/user')
            .then(res=>{
               if(res.data.success){
                    this.allusers = res.data.docs;
               }
            })
            .catch(err=> alert(err));
    },
    methods: {
        //deleting the user
        deleteUser(username){
            axios.delete(`http://localhost:5000/moderator/deletebymoderator/${username}`)
                .then(res => {
                    if(res.data.success){
                        alert("successfully deleted");
                        axios.get('http://localhost:5000/users/user')
                            .then(res=>{
                            if(res.data.success){
                                    this.allusers = res.data.docs;
                            }
                            })
                            .catch(err=> alert(err));

                    }
                })
                .catch(err=> alert(err));
        }
    }
}
</script>
<style scoped>

#followbtn{
    background-color: white;
    color: green;
    border-radius: 20px;
    font-weight: bold;
    border: 2px solid green;
    float: right;
    width: 100px;
}

#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   vertical-align:top  ;
   border: 3px solid lightgreen;
 
}
</style>