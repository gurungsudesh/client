<template>
    <div>
        <div  id ="tabs">
            <ul class="nav nav-tabs justify-content-center"  id="myTab" role="tablist">
                    <li class="nav-item">
                        <a class="nav-link active" id="home-tab" data-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true">Timeline</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" id="follower-tab" data-toggle="tab" href="#follower" role="tab" aria-controls="follower" aria-selected="false">Followers</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link" id="following-tab" data-toggle="tab" href="#following" role="tab" aria-controls="following" aria-selected="false">Following</a>
                    </li>
                    </ul>
                    <div class="tab-content" id="myTabContent">
                    <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">...</div>
                    <div class="tab-pane fade" id="follower" role="tabpanel" aria-labelledby="follower-tab">...</div>
                    <div class="tab-pane fade" id="following" role="tabpanel" aria-labelledby="following-tab">...</div>
                    </div>
                
            </div>
    </div>
</template>
<script>
export default {
    name: "UPTimeline"
}
</script>
<style scoped>
    #tabs a{
        margin-top: 5%;
    color: green;
    font-size: 15px;
    font-weight: bold;
}
</style>