<template> 
    <div> 

        <div class="usermain" ref="userid" id="userid">
            <div class="top">
                Forgot your Password?
            </div>
            <div class="middle" >
                 <div class="formmain">
                    <form @submit="onSubmit1" autocomplete="off">
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">
                                <label style="font-size:18px; font-weight:bold; color:green; padding:5px; ">Enter your username:</label>
                                <input type="text" class="form-control"  id="inputPassword3" v-model="username"  required>
                            </li>
                             <li class="list-group-item" > 
                                    <button style="margin-left:35%; margin-top:10px;" type="submit" class="btn btn-success">Next</button> 
                                </li>
                        </ul>
                    </form>
                 </div>    

            </div>
        </div>


        <div class="middlemain" ref="middleid" id="middleid">
            <div class="top">
                Answer your security question
            </div>
            <div class="middle" >
                 <div class="formmain">
                    <form @submit="onSubmit2" autocomplete="off">
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">
                                    <input type="text" ref="inputtext1" id="inputtext1" :readonly="true" v-model="poke1">
                                    <input type="text" class="form-control"  id="inputPassword3" placeholder="Answer 1" required>
                                </li>

                                <li class="list-group-item">
                                     <input type="text" ref="inputtext1" id="inputtext1" :readonly="true" v-model="poke2">
                                    <input type="text" class="form-control"  id="inputPassword3"  placeholder="Answer 2" required>
                                </li>
                                <li class="list-group-item" > 
                                    <button style="margin-left:35%; margin-top:20px;" type="submit" class="btn btn-success">Next</button> 
                                </li>
                        </ul>
                    </form>
                 </div>    

            </div>
        </div>

        <div class="nextmain" ref="nextid" id="nextid">
            <div class="top">
                Write your new password
            </div>
            <div class="middle">
                 <div class="formmain">
                    <form @submit="onSubmit3" autocomplete="off">
                        <ul class="list-group list-group-flush">

                                <li class="list-group-item">
                                    <span style="font-size:18px; font-weight:bold; color:green; padding:10px;">New Password:</span>
                                    <input type="text" class="form-control"  id="inputPassword3"  required>
                                </li>
                                <li class="list-group-item">
                                    <span style="font-size:18px; font-weight:bold; color:green; padding:10px;">Confirm Password:</span>
                                    <input type="text" class="form-control"  id="inputPassword3"  required>
                                </li>
                                <li class="list-group-item" > 
                                    <button style="margin-left:35%; margin-top:20px;" type="submit" class="btn btn-success">Confirm</button> 
                                </li>
                        </ul>
                    </form>
                 </div>    

            </div>
        </div>
    </div>
</template>
<script> 
export default {
    name: "birsiyoPassword",
    data(){
        return{
            key1:'',
            key2:'',
            poke1:'my name is',
            poke2:'my name is'
        }
    },
    methods: {
        onChange1(event) {
            alert(event.target.value);
        },
        onChange2(event) {
            alert(event.target.value);
        },
        onSubmit1(){
             var vm = this;          
        
            vm.$refs.userid.style.opacity = '0';
            vm.$refs.userid.style.left = '5%';
            vm.$refs.middleid.style.visibility= 'visible';
            vm.$refs.middleid.style.opacity = '100';
              
        },
        onSubmit2(){
          var vm = this;
                    
            vm.$refs.middleid.style.opacity = '0';
            vm.$refs.middleid.style.left = '5%';
            vm.$refs.nextid.style.visibility= 'visible';
            vm.$refs.nextid.style.opacity = '100';     
  
        },
        onSubmit3(){
            alert('done');
        }
    }
}
</script>
<style scoped>
    .middlemain{
    position: absolute;
    top:10%;
    left:38%;
    width:25%;
    height:70%;
    border: 1px solid lightgreen;
    background-color: white;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
    
        visibility: hidden;
    opacity:0;
    transition: 0.5s;
    }
    .nextmain{
    position: absolute;
    top:10%;
    left:38%;
    width:25%;
    height:70%;
    border: 1px solid lightgreen;
    background-color: white;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
        
        visibility: hidden;
    opacity: 0;
    transition: 0.5s;
    }
    .usermain{
    position: absolute;
    top:10%;
    left:38%;
    width:25%;
    height:40%;
    border: 1px solid lightgreen;
    background-color: white;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
    opacity: 100;
    transition: 0.5s;
    }
    .top{
        padding: 10px;
        font-size: 25px;
        color:green;
        text-align: center;
        font-weight: bold;
        border-bottom: 1px solid green;
        
    }
    .middle{
        margin-top:20px;
        padding: 10px;
    }
    #inputtext,  #inputtext1, #inputtext3{
        color: black;
        width: 400px;
        outline: none;
        background: none;
        border: none;
        padding: 5px;
        border-radius: 10px;
        font-weight: bold;
    }
</style>