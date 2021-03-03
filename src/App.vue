<template>
  <div id="nav">
   

  </div>
  <router-view  @addPost="add" />
</template>
<script>

export default {
    
 
}
</script>


<style>
body{
  background: rgb(243, 240, 240);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #555;
  
  
}

#nav {
  padding: 30px;
  text-align: center;
  
}

#nav a {
  font-weight: bold;


}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
