<template> 
    <div> 
        <div class="middlemain">
            <div class="top">
                Answer your security question
            </div>
            <div class="middle">
                 <div class="formmain"  >
                    <form @submit="onSubmit" autocomplete="off">
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">
                                    <select  class="custom-select" @change="onChange1($event)" v-model="key1" style="color:darkgray; border:none; border-bottom:1px solid lightgray;">
                                    <option  value="" disabled selected >Choose your Security Question</option>
                                        <option  value="1">Option 1</option>
                                        <option  value="2">Option 2</option>
                                        <option  value="3">Option 3</option>
                                    </select>
                                </li>
                                <li class="list-group-item">
                                    <input type="text" class="form-control"  id="inputPassword3" placeholder="Answer 1" required>
                                </li>

                                <li class="list-group-item">
                                    <select class="custom-select" @change="onChange2($event)" v-model="key2" style="color:darkgray; border:none; border-bottom:1px solid lightgray;">
                                    <option value="" disabled selected style="color:lightgray">Choose your next Security Question</option>
                                        <option value="1">Option 1</option>
                                        <option value="2">Option 2</option>
                                        <option value="3">Option 3</option>
                                    </select>
                                </li>
                                <li class="list-group-item">
                                    <input type="text" class="form-control"  id="inputPassword3"  placeholder="Answer 2" required>
                                </li>
                                <li class="list-group-item" > 
                                    <button style="margin-left:35%; margin-top:20px;" type="submit" class="btn btn-success">Sign Up</button> 
                                </li>
                        </ul>
                    </form>
                 </div>    

            </div>
        </div>

        <div class="nextmain">
            <div class="top">
                Write your new password
            </div>
            <div class="middle">
                 <div class="formmain"  >
                    <form @submit="onSubmit" autocomplete="off">
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
                                    <button style="margin-left:35%; margin-top:20px;" type="submit" class="btn btn-success">Sign Up</button> 
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
            key2:''
        }
    },
    methods: {
        onChange1(event) {
            alert(event.target.value);
        },
        onChange2(event) {
            alert(event.target.value);
        }
    }
}
</script>
<style scoped>
    .middlemain{
    position: absolute;
    top:20%;
    left:38%;
    width:25%;
    height:70%;
    border: 1px solid lightgreen;
    background-color: white;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
    }
    .nextmain{
    position: absolute;
    top:20%;
    left:70%;
    width:25%;
    height:70%;
    border: 1px solid lightgreen;
    background-color: white;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 5px 10px 5px rgb(131, 143, 131) ;  
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
</style>