<template>
    <div>
        <div class="topleft">
            <form class="form-inline" id="fromsearch">
                    <input class="form-control" style="width: 300px" type="search" placeholder="Search" aria-label="Search">
                    <button id="sbtn" class="btn btn-success" type="submit"><i class="fas fa-search" ></i></button>
            </form>
        </div>
        <div class="bottomleft">
            <div class="messagingpeople">
                <img src="../../../../images/ProfilePic.jpg"><span style="font-size: 20px">Prashant Dhoju</span> 
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Searchchat",
    data(){
    return {
        
    }
  },
  methods:{
      
      }
    
}
</script>
<style scoped>
    .bottomleft img{
            border-radius: 50%;
            width: 50px;
            height: 50px;
            margin-right: 10px;
        }
        .topleft{
            position:absolute;
            top: 0px;
            width: 100%;
            height:10%;
            
        }
        #fromsearch{
            position: absolute;
            margin-top:15px;
            margin-left: 20px;
        }
        .bottomleft{
            position: absolute;
            bottom:0px;
            height:90%;
            width:100%;
            padding: 5px;
           
        }
        .messagingpeople{
            width: 100%;
            background-color: rgb(192, 247, 175);
            margin-top: 20px;  
            border-radius: 20px;
        }
</style>