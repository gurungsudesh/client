<template>
  <div class="home">
    
   <LoginRightside/>
    <LoginForm />
    <SignUp />
  </div>
</template>

<script>
// @ is an alias to /src
import LoginRightside from '../components/LoginRightside'
import LoginForm from '../components/LoginForm'
import SignUp from '../components/SignUp'
export default {
  name: 'home',
  components: {
    LoginForm,
    LoginRightside,
    SignUp
  }
}
</script>

<style scoped>
  *{
    color: blue;
  }
</style>
