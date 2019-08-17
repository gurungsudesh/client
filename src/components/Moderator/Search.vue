<template>
    <div>
        <div class="container" id="topsearch">
                      
                      <nav style="font-weight:bold; background-color: green">
                            <div >
                                <form id="searchbtn" class="form-inline ">
                                <input class="form-control mr-sm-2" type="search"  placeholder="Search" aria-label="Search">
                                <button class="btn btn-success" type="submit">Search</button>
                                <div id="dpdn" class="btn-group">
                                    <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                    </button>
                                    <div  class="dropdown-menu dropdown-menu-right">
                                        <router-link class="dropdown-item" to="/" >Profile</router-link>
                                        <router-link class="dropdown-item" to="/" >Settings</router-link>
                                        <button v-on:click="logout"><router-link class="dropdown-item" to="/">Log Out</router-link></button>
                                    </div>
                                    </div>
                                </form>
                            
                          </div>
                        </nav> 
        </div>   
         
    </div>
                       
    
    
</template>

<script>
export default {
    name:"Search"
}
</script>
 <style scoped>
 #topsearch{
     position: absolute;
     text-align: right;
     
      }
      #searchbtn{
          position: absolute;
          right: 10px;
          margin-top: 2%;
      }




#btnstats{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
}
#dpdn{
    margin-left: 10px;
}
 #dpdn a{
   font-size: 14px;
    margin-left: 0px;
    
}
#dpdn a:active{
  background-color: green;
    
}
</style>



