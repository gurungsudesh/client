<template>
<div class="homemain">
  <div class="home">
    <div class="Rightside">
   <LoginRightside/>
    <div class="leftside">
    <LoginForm />
    <SignUp />
    </div>
    <div class="footer">
                    <div id="bcont">
                        <p>Develop by: Prashant Dhoju, Shishir Kumar Gurung and Sudesh Gurung</p>
                    </div>
                </div>

  </div>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
import LoginRightside from '../components/Login/LoginRightside'
import LoginForm from '../components/Login/LoginForm'
import SignUp from '../components/Login/SignUp'

export default {
  name: 'home',
  components: {
    
    LoginRightside,
    LoginForm,
    SignUp,
   
  }
}
</script>

<style scoped>
.homemain{
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(to bottom, rgb(238, 212, 212) ,  rgb(136, 46, 46));
}
.home{
  position: absolute;
  top: 10%;
  left: 10%;
  width: 80%;
  height: 80%;
  border-radius: 20px;
  
   
}
.Rightside{
   background-color: rgb(56, 0, 0);
    width: 100%;
  height: 100%;
  position: absolute;
  
   
}
.leftside{
  position: absolute;
    background-color: white;
    width: 50%;
    height: 100%;
    right: 0%;
}
.footer{
    position: absolute;
     bottom: 0px;
    background: lightgray;
    height: 3%;
   
    width: 100%;
}
#bcont{
  font-size: 10px;
    font-weight: bold;
    padding-left: 25%;
}
</style>
