<template>
    <div>
        <div class="top">
            <NavBar/>
        </div>
        <div class="mainbody">
            <Noticontent/>
        </div>
    </div>

</template>

<script>
import NavBar from '../components/UserHome/NavBar'
import Noticontent from '../components/UserHome/Notification/Noticontent'
export default {
    name:'notification',
    components: {NavBar,Noticontent}
}
</script>

<style>

</style>