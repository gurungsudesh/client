<template>
    <div>
        <UserInfo/>
        <Search/>
        <Posts/>
    </div>
</template>

<script>
import Posts from "../components/Moderator/Posts"
import Search from '../components/Moderator/Search'
import UserInfo from '../components/Moderator/UserInfo'
export default {
    name: "Moderator",
    components: {
        UserInfo,
        Search,
        Posts
    }
}
</script>

<style>

</style>
