<template>
  <div class="home">
    <div class="Rightside">
   <LoginRightside/>
    <div class="leftside">
    <LoginForm />
    <SignUp />
    </div>
  </div>
  <div class="footer">
                    <div id="bcont">
                        Develop by: Prashant Dhoju, Shishir Kumar Gurung and Sudesh Gurung
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

.Rightside{
   background-color: rgb(56, 0, 0);
    width: 100%;
  height: 96%;
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
    font-weight: bold;
    padding-left: 25%;
}
</style>
