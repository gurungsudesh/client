<template>
    <div>
<<<<<<< HEAD
        <div class="container">
            <div class="m_leftside" >
                    <div class="m_topl">
                            <div class="row">
                                    <div  class="col-md-auto">
                                      <img src="bullet.jpg" >
                                            
                                            <h3>Username gurung</h3>
                                            <div id="m_lcontent">
                                            <i class="fas fa-user-check"></i>
                                            Verified                                                
                                               
                                            </p>
                                            <button id="btn" class="btn btn-success"  >Edit Profile</button>
                                        </div>
                                    </div>
                            </div>    
                    </div>
                    
                        
                    
                    </div>
            </div>
=======
        <UserInfo/>
        <Search/>
        <Posts/>
>>>>>>> bfc4b172794f4bc257080a2d52a0bf74ccd699f2
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
