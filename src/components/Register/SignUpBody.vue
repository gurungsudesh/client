<template>
    
        <div class="cropmain"> 
            <div class="rightside">
                <div id ="content">
                    
                    <i class="fa fa-home" style="font-size:60px; position: relative; top:10% "></i>
                     <h1> Get Started </h1>
                     <h2> With Ipost</h2>
                    
                     <br>
                     <br>
                     

                     
                </div>
            </div>
            <div class="leftside">
                <div id="leftcontent">
                <i class="fa fa-hand-point-down" style="font-size:60px;"></i>
                <br>
                <h2>Sign Up</h2>    
                <RegisterForm/>
                </div>
            </div>
        </div>
    
</template>

<script>
import RegisterForm from '../Register/RegisterForm';
export default {
    name: "SignUpBody",
    components: {
        RegisterForm
    }
}
</script>

 <style scoped>
 #content{
     position: relative;
     text-align: center;
     bottom:10%;
     
     color: white;
 }
.cropmain{
    top:10%;
    left:15%;
    position: absolute;
    width: 70%;
    height:80%;
    
    border-radius: 20px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
}
.rightside{
    position: absolute;
    left: 0%;
     width: 50%;
     height: 100%;
    background-color: rgb(96, 235, 96);
    border-radius: 20px 0px 0px 20px;
     
}
.leftside{
    position: absolute;
    right:0px;
    width: 50%;
    height: 100%;
    background-color: white;
    border-radius: 0px 20px 20px 0px;
    
    
}
#leftcontent{
    position: relative  ;
    color: rgb(115, 206, 115);
    text-align: center;
    margin-top: 10%;
}
</style>
