<template>
  <div class="main">
    <div class="action">
      <div class="h" @click="show">{{ post}}</div>
      <div>
        <span class="material-icons" @click="deletePost">
          delete
        </span>
        <span class="material-icons">
          done
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

<style scoped>
.main {
  background: rgb(250, 248, 248);
  margin-bottom: 5px;
  padding: 10px;
}
.h {
  cursor: pointer;
  padding: 2px;
}
span {
  cursor: pointer;
  margin-left: 10px;
  color: rgb(131, 127, 127);
}
span:hover {
  color: rgb(27, 26, 26);
}
.action {
  display: flex;
  justify-content: space-around;
  align-items: center;
}
</style>
