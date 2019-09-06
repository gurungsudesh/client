<template>
    <div>
        <div class="shomebody">
            <div class="mainbody">
                <div class="topmain">
                    <h3 style="color: green"><i class="fas fa-user-cog" style="margin-right: 10px;"></i>Account Settings</h3>
                </div>
                <ul>
                <li ref="generalli" id="generalli" >
                    <div class="middlemain">
                    <h5 @click="showgeneral() ;textareaResize(); " > <i class="fas fa-cog" style="margin-right: 10px;"></i>General Info</h5>
                    <div class="accountinfo" ref="generalid" id="generalid">
                    <table style="border-top:1px solid gray;" >
                        <tr>
                            <td style="width: 20%;  ">
                                <div class="option1">
                                    <span class="title1">Full Name</span>
                                    
                                </div>
                            </td>
                            <td>
                                <div class="showname">
                                        <span class="title2">
                                        <input type="text" ref="inputtext" id="inputtext" :readonly="shouldDisable1" v-model="changeName"></span>
                                </div>
                            </td>
                            <td  style="width: 20% ;text-align: center;">
                                 <a  class="edit" @click="editable('1')" href="#">Edit</a>
                            </td>
                        </tr>
                        <tr>
                            <td style="width: 20%;  ">
                                <div class="option1">
                                    <span class="title1">Address</span>
                                    
                                </div>
                            </td>
                            <td>
                                <div class="showname">
                                        <span class="title2">
                                        <input type="text" ref="inputtext" id="inputtext" :readonly="shouldDisable4" v-model="changeAddress"></span>
                                </div>
                            </td>
                            <td  style="width: 20% ;text-align: center;">
                                 <a  class="edit" @click="editable('4')" href="#">Edit</a>
                            </td>
                        </tr>
                        <tr>
                             <td>
                                <div class="option2">
                                    <span class="title1">Email</span>
                                </div>
                            </td>
                            <td>
                                <div class="showemail">
                                        <span class="title2">
                                        <input type="text" ref="inputtext1" id="inputtext1" :readonly="shouldDisable2" v-model="changeEmail">
                                        </span>
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <a class="edit" @click="editable('2')"  href="#">Edit</a>
                            </td>
                        </tr>
                        <tr>
                            <td valign="top" >
                                <div class="option3">
                                    <span class="title1">User Bio</span>
                                </div>
                            </td>
                            <td>
                                    <div class="showemail">
                                            <span class="title2">
                                            <textarea @input="textareaResize"  :readonly="shouldDisable3" ref="textarea1" id="textarea1"  v-model="changeUserbio"> </textarea>
                                            </span>
                                        </div>
                            </td>
                            <td style="text-align: center;" valign="top">
                                <a class="edit" @click="editable('3')" href="#">Edit</a>
                            </td>
                        </tr>
                        <tr>
                            <td></td>
                            <td></td>
<<<<<<< HEAD
                            <td style="text-align: right;"><button @click ="confirmBio" class="btn btn-success">Save Changes</button></td>
=======
                            <td style="text-align: right;"><button  class="btn btn-success">Save Changes</button></td>
>>>>>>> 1f80ca0845ad257ce569923b2c5211851a3c0b5c
                        </tr>
                      
                    </table>
                    </div>
                </div></li>
                <li ref="passwordli" id="passwordli">
                 <div class="changep" >
                        <h5 @click="showpassword()" ><i class="fas fa-cog" style="margin-right: 10px;"></i>Change Password</h5>   
                        <div class="changepassword" ref="passwordid" id="passwordid">
                            <form>
                        <table style="border-top:1px solid black;">
                         <tr>
                            <td style="width: 20% ; font-weight: 600" >Previous Password:</td>
                            <td > <input type="text" class="form-control"></td>

                        </tr>
                        <tr>
                            <td style="font-weight: 600">New Password:</td>
                            <td><input type="text" class="form-control"></td>
                        </tr>
                         <tr>
                            <td style="font-weight: 600">Confirm Password:</td>
                            <td><input type="text" class="form-control"></td>
                         </tr>
                         <tr>
                             <td></td>
                             
                             <td style="text-align: right;"><button type="submit" class="btn btn-success">Save Changes</button></td>
                         </tr>
                    </table>
                </form>
                        </div>
                 </div>
                </li>
                <li>
                 <div class="deactivate">
                     <h5><i class="fas fa-cog" style="margin-right: 10px;"></i>Deactivate Account</h5>
                 </div>
                </li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Accountdata",
    data(){
    return {
        username:'',
        commenting:'',
        changeName:'',
        changeEmail:'',
        changeUserbio:'ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssadjoaisdjaosidjaoisjdoiasjdooisjd',
        changeAddress:'Ranipauwa',
        shouldDisable1:true,
        shouldDisable2:true,
        shouldDisable3:true,
        shouldDisable4:true,
    }
  },
  methods:{
      confimBio(){

      },
      editable(value){
                    this.$refs.textarea1.style.height=this.$refs.textarea1.scrollHeight+'px';
                    switch(value){
                        case "1":
                            if(this.shouldDisable1){
                                this.shouldDisable1=!this.shouldDisable1;
                                this.$refs.inputtext.style.backgroundColor='white';
                                this.$refs.inputtext.style.color='black';
                                this.$refs.inputtext.style.padding='8px';
                            }else{
                                this.shouldDisable1=!this.shouldDisable1;
                                this.$refs.inputtext.style.background='none';
                                this.$refs.inputtext.style.color='grey';
                                this.$refs.inputtext.style.padding='5px';
                                alert('Changes Saved');
                                
                            }
                            return;

                        case "2":
                            if(this.shouldDisable2){
                                this.shouldDisable2=!this.shouldDisable2;
                                this.$refs.inputtext1.style.backgroundColor='white';
                                this.$refs.inputtext1.style.color='black';
                                this.$refs.inputtext1.style.padding='8px';
                                
                            }else{
                                this.shouldDisable2=!this.shouldDisable2;
                                this.$refs.inputtext1.style.background='none';
                                this.$refs.inputtext1.style.color='grey';
                                this.$refs.inputtext1.style.padding='5px';
                                
                                alert('Changes Saved');
                            }
                            return;
                            
                        case "3":
                        
                        if(this.shouldDisable3){
                                this.shouldDisable3=!this.shouldDisable3;
                                this.$refs.textarea1.style.backgroundColor='white';
                                this.$refs.textarea1.style.color='black';
                                

                                
                            }else{
                                this.shouldDisable3=!this.shouldDisable3;
                                this.$refs.textarea1.style.background='none';
                                this.$refs.textarea1.style.color='grey';
                                alert('Changes Saved')
                            }
                            return;
                            
                        case "4":

                        if(this.shouldDisable4){
                                this.shouldDisable4=!this.shouldDisable4;
                                this.$refs.textarea1.style.backgroundColor='white';
                                this.$refs.textarea1.style.color='black';
                                

                                
                            }else{
                                this.shouldDisable4=!this.shouldDisable4;
                                this.$refs.textarea1.style.background='none';
                                this.$refs.textarea1.style.color='grey';
                                alert('Changes Saved');
                            }
                            return;
                    }
                },
             
              showgeneral:function(){
                  var vm = this;
                 
                  if(vm.$refs.generalid.style.display == "block"){
                    vm.$refs.generalid.style.display = 'none'
                    vm.$refs.generalli.style.backgroundColor = 'white';
                  }
                  else{
                    vm.$refs.generalid.style.display = 'block';
                    vm.$refs.generalli.style.backgroundColor = 'rgb(223, 255, 225)';
                  }
              },
              showpassword:function(){
                  var vm = this;
                  if(vm.$refs.passwordid.style.display == 'block'){
                   vm.$refs.passwordid.style.display = 'none'
                    vm.$refs.passwordli.style.backgroundColor = 'white';
                  }
                  else{
                     vm.$refs.passwordid.style.display = 'block';
                    vm.$refs.passwordli.style.backgroundColor = 'rgb(223, 255, 225)';
                  }
              },
              textareaResize:function() {
                  this.$refs.textarea1.style.height=this.$refs.textarea1.scrollHeight+'px';
                }
              
  }
    
}
</script>
<style scoped>
table{
        width: 100%;
    }
    .shomebody{
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgb(203, 255, 207);
        
    }
    .mainbody{
        border-left: 1px solid green;
        border-right: 1px solid green;
        position: absolute;
        padding: 20px;
        left: 10%;
        width: 80%;
        height: 100%;
        background-color: white;
    }
    table td{
        padding: 5px;
        padding-top: 10px;
        
    }
    .middlemain{
        padding-top: 5px;
    }
    
    
    .title1{
        width:300px;
        
    }
    .title2{
        width:500px;
    }
    #textarea1{
        outline: none;
        background: none;
        width: 500px;
        border: none;
        resize: none;
        height: auto;
        color: grey;
        padding-bottom: 8px;
        padding-left: 8px;
        padding-right: 8px;
        border-radius: 20px;
    }
    #generalid td{
        border-bottom: 1px solid rgb(162, 194, 165);
    }
    
    #passwordid{
        display: none;
        margin-left: 20px;
        
    }
    #passwordid input[type="text"]{
        width: 400px;
        border-radius: 20px;
        border: 1px solid gray;
        outline: none;
        padding: 5px;
        font-size: 13px;
    }
    #generalid{

        display: none;
        margin-left: 20px;
        padding: 5px;
        
    }
    
    #inputtext,  #inputtext1 {
        color: gray;
        width: 400px;
        outline: none;
        background: none;
        border: none;
        padding: 5px;
        border-radius: 10px;
    }
    
        
    .topmain{
        padding-left: 10px;
    }
    .title1{
        font-weight: 600;
    }
    .title2{
        font-size: 14px;
    }
    h5{
        padding-left: 20px;
        padding-top: 5px;
        padding-bottom: 5px;
        color: green;
    }
    h5:hover{
        background-color: rgb(179, 224, 174);
        cursor: pointer;
    }
    ul{
        list-style-type: none;
        margin: 0;
        padding: 0;
        border-top:1px solid gray;
        border-bottom:1px solid gray;
    }
    .edit{
        color: green;
        font-weight: 600;
        font-size: 12px;
    }
    .edit:hover{
        text-decoration: none;
    }
    button{
        border-radius: 20px;
        font-weight: 600;
        color: green;
        background-color: white;
        margin: 10px;
    }

</style>