<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-auto">
                    <img src="../../../../images/ProfilePic.jpg" >
                </div>
                <div class="col-md-auto">
                    <h3>Username gurung</h3>
                        <p class="text-left" style="color: gray; font-size: 12px" >Made at janaury 2016 
                            <br>
                            99 followers<br>
                            99 following<br>
                            
                        </p>
                        <button id="btn" class="btn btn-success" >Follow</button>
                </div>
            </div> 
        </div>
    </div>
</template>
<script>
export default {
    name: "UPInfo"
}
</script>
<style scoped>
    #btn{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
     
}
img{
    width: 100px;
    height: 100px;
    border-radius: 50%;
    border: 10px solid rgb(158, 221, 158);

}
</style>