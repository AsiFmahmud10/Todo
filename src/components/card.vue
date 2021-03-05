<template>
  <div class="main">
    <div class="action">
      <div class="h" @click="show">{{ post}}</div>
      <div class="flex">
        <span class="material-icons effect" @click="deletePost">
          delete
        </span>
       
      </div>
    </div>
    <div v-if="on" style="display:flex-root">
      {{ post.body }}
    </div>
  </div>
</template>

<script>

export default {
  props: ["post"],
  
  setup(props, {emit}){
     const deletePost = ()=>{
        console.log(props.post);
         emit("deletePost", props.post)
     }
    return {deletePost}
  },
  
};
</script>

<style >
.main {
  background: rgb(250, 248, 248);

  padding: 10px;
    max-width: 640px;
   margin: 3px auto;
   
}
.h {
  cursor: pointer;
  padding: 12px;
  margin-left: 13px;
}
.effect {
  cursor: pointer;
  margin-left: 10px;
  color: rgb(131, 127, 127);
}
.effect:hover {
  color: rgb(27, 26, 26);
}
.action {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.flex{
      margin-right: 23px;
}
</style>


 .toast-enter-active {
    animation: wobble 0.5s ease;
  }
  /* leave transitions */
  .toast-leave-to {
    opacity: 0;
    transform: translateY(-60px);
  }
  .toast-leave-active {
    transition: all 0.3s ease;
  }
  @keyframes wobble {
    0% { transform: translateY(-100px); opacity: 0 }
    50% { transform: translateY(0px); opacity: 1 }
    60% { transform: translateX(8px); opacity: 1 }
    70% { transform: translateX(-8px); opacity: 1 }
    80% { transform: translateX(4px); opacity: 1 }
    90% { transform: translateX(-4px); opacity: 1 }
    100% { transform: translateX(0px); opacity: 1 }
  }