<template>
    <div>
        <div class="container" id="topsearch">
                      
                      <nav style="font-weight:bold; background-color: green">
                            <div >
                                <form id="searchbtn" class="form-inline ">
                                <input class="form-control mr-sm-2" type="search"  placeholder="Search" aria-label="Search">
                                <button class="btn btn-success" type="submit">Search</button>
                                <button v-on:click="logout()" style="margin-left:5px;" class="btn btn-success" type="button"><i class="fas fa-sign-out-alt" ></i></button>
                                </form>
                            
                          </div>
                        </nav> 
        </div>   
         
    </div>
                       
    
    
</template>

<script>
export default {
    name:"Search",
    methods: {
        logout(){
        localStorage.removeItem('moderatorToken')
        this.$router.push("/");
      }
    }
}
</script>
 <style scoped>
 #topsearch{
     position: absolute;
     right:10px;
     text-align: right;
     width: 100%;
     margin-top:10px;
     
      }
      #searchbtn{
          position: absolute;
          right: 10px;
          
      }




#btnstats{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
}


</style>



