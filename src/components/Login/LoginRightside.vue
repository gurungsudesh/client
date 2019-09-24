<template>
                <div id="content">
                    <img src="../../../images/das.png" >
                    <br>
                    <div id="blah">
                    - Search the controversial subject<br><br>
                    - Present your opinion<br><br>
                    - Follow People<br><br>
                    </div>
   
    </div>
</template>

<script>
export default {
    name: "LoginRightside"
}
</script>

<style scoped>

#content{
    color: white;
    position: absolute;
    height: auto;
    top:0%;
    left: 5%;
    font-size: 20px;
    font-weight: bold;
}
img{
    margin-top:10%;
    margin-left:10%;
    margin-bottom: 5%;
    border-radius: 50%;
    height:30%;
    width:30%;
    transition: 0.5s;
    
}
#blah{
    transform: scale(1);
    transform-origin: 0 0;
    transition: 0.5s;
}
@media only screen and (max-width: 1000px) {
    img{
        margin-left:0%;
    }
}
@media only screen and (min-height: 550px) and (max-height: 600px) {
    img{
        margin-top:2%;
    }
    #blah{
        transform: scale(0.9);
    }

}
@media only screen and (min-height:0px) and (max-height: 550px) {
    img{
        margin-top:2%;
    }
    #blah{
        transform: scale(0.9);
        opacity: 0;
    }

}
</style>
