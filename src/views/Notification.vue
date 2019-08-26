<template>
    <div>
        <div class="mainbody">
            <div class="home-header">
                <NavBar/>
            </div>
            <div class="homebody">
                <Noticontent/>
            </div>
        </div>
    </div>

</template>

<script>
import NavBar from '../components/UserHome/NavBar'
import Noticontent from '../components/UserHome/Notification/Noticontent'
export default {
    name:'Notification',
    components: {NavBar,Noticontent}
}
</script>

<style>

</style>