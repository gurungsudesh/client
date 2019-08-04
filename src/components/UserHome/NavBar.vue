<template>
    <div> 
        <div id="menu">
                <a href="home.html">Home</a>
                <a href="notification.html">Notifications</a>
                <a href="">Messages</a>
            </div>
            <div class ="home-search">
                    
                <input type="search" value="Search ">
                <input type="submit" value="Search">
                <img src="bullet.jpg" id="otherprofileicon" >
                <button> <router-link to="/">Log Out</router-link></button>
            </div>
       
    </div>
</template>

<script>
export default {
    name: "NavBar"
}
</script>

<style>
#menu{
    position: absolute;
    top:0px;
    left: 0px;
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 10px;
    padding-top: 20px;
}
#menu a{
   font-family: Arial, Helvetica, sans-serif;
    background-color: lightgrey;
    font-size: 20px;
    color: rgb(56, 0, 0);
    text-decoration: none;
    padding-left: 30px;
    padding-right: 30px;
    padding-bottom: 5px;
    padding-top: 5px;
    border-radius:20px;
    margin:10px;
}
#menu a:hover{
    background-color: gray;
}
.home-search{
    position: absolute;
    top:0px;
    right: 0px;
    padding-top:10px;
    }
#otherprofileicon{
    
    border-radius: 50%;
   width: 40px;
   height: 40px;
   margin-right: 10px;
   vertical-align:top  ;
   border: 3px solid darkgrey;
  
  
}
input[type="search"]{
    background-color: white;
    width: 200px;
    margin: 10px;
    border: 1px solid black;
    border-radius:20px;
    padding: 5px;
    outline:none;
}
input[type="submit"] {
    background-color: lightgray;
    font-size: 15px;
    font-weight: bold;
    padding: 5px;
    padding-left: 15px;
    padding-right: 15px ;
    margin-left: 5px;
    margin-right: 5px;
    border-radius: 10px;
    color:rgb(56, 0, 0);
    border: none;
    vertical-align:middle;
    
}
input[type="submit"]:hover{
background-color: gray;
}
</style>
