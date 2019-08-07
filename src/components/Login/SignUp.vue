<template>
     
                <div class="down">
                        <div id="downside">
                                    <h1>Want to share<br>
                                     your views</h1>
                                    <h2>to the world?</h2>   
                                    <h5>Join iPost Now.</h5>
                         
                            <br>
                                    <button class="btn btn-success" id="submit1"  ><router-link id="routsubmit" to="/signup">Sign Up</router-link></button><br><br>                                      
                            
                        </div>
                </div>
</template>

<script>

export default {
    name: "SignUp"
   
}
</script>

 <style scoped>



.down{
    position: absolute;
    bottom: 10%;
    
}
#downside{
    color: rgb(31, 73, 31);
    text-align: left;
    padding-left: 50px;
}
button[type="submit"] {
    
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
