<template>
    <div> 
      
                <div class="profileinfo">
                    
                    <div class="profilename">
                        <div id="profilename1">
                        <img src="bullet.jpg" id="profileicon" >Hi. {{name}}
                    </div>
                    </div>              
                    </div>
    </div>
</template>

<script>
import jwtDecode from 'jwt-decode'
export default {
    name : "UserInfo",
    data(){
        const token = localStorage.usertoken
        const decode = jwtDecode(token)
        return{
            name : decode.name
        }
    }
}
</script>

<style scoped>


#profilename1{
    font-family: Arial, Helvetica, sans-serif;
    margin-top:20px;
   margin-left: 15px;
    font-size: 25px;
    font-weight: 600;
    color: rgb(8, 66, 13);
    
    
    
}
#profileicon{
    
     border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-right: 10px;
    vertical-align:middle;
    border: 5px solid rgb(146, 209, 150);
   
   
}


</style>
