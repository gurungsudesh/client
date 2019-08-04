<template>
     
                <div class="down">
                        <div id="downside">
                            
                           
                               
                                    <p style="font-size: 30px">Want to share your views <br>
                                    to the world?<br><br>
                                    </p>
                               
                                    <p style="font-size: 20px">Join iPost Now.
                                </p><br>
                            
                                    <a href=""><button type="submit" id="submit1" name="submit" ><router-link id="routsubmit" to="/signup">Sign Up</router-link></button></a><br><br>                                      
                            
                        </div>
                   
                               
                </div>
       
   
</template>

<script>

export default {
    name: "SignUp"
   
}
</script>

<style>
.down{
    position: absolute;
    bottom: 10%;
    right:40%;
}
#downside{
    color: rgb(56, 0, 0);
    font-size: 10px;
    padding-left: 50px;
}
button[type="submit"] {
    background-color: rgb(56, 0, 0);
    
    padding: 5px;
    padding-right: 10px;
    padding-left: 10px;
    border-radius: 10px;
    color:white;
    border: none;
    margin-left: 10px;
}
#routsubmit{
     color:white;
     font-size: 15px;
    font-weight: bold;
    text-decoration: none;
}
#submit1{
    width: 300px;
}

</style>
