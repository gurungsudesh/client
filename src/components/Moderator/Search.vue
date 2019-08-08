<template>
    <div>
         <div class="m_mainright">
                    <div class="m_topr">
                        

                            <nav class="navbar navbar-expand-lg navbar-light" style="font-weight:bold; background-color: white">
                                    <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
                                    
                                    
                            <form id="searchbtn" class="form-inline my-2 my-lg-0">
                              <input class="form-control mr-sm-2" type="search"  placeholder="Search" aria-label="Search">
                              <button class="btn btn-success" type="submit">Search</button>
                            </form>
                          
                          </div>
                        </nav> 
                          
                    </div>
            </div>
    </div>
</template>

<script>
export default {
    name:"Search"
}
</script>
 <style scoped>
.m_topr{
 
    margin-top:2%;
    display: block;
  

    margin-left: 65%;
    
} 
#searchbtn{
    display: inline-block;
    
}
.m_mainright{
    border-bottom:1px solid lightgrey;
}

#btnstats{
    background-color: white;
     color: green;
     font-weight: 700; 
     border-radius: 20px;
     width:150px;
}
</style>



