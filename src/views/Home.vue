<template>
  <div class="container">
    <transition name="toast">
      <Toast v-if="show" />
    </transition>

    <div class="inputWraper">
      <input
        class="input"
        type="text"
        placeholder="Enter to add task "
        @keypress.enter="addTask"
        v-model="input"
      />
    </div>
              <div v-if="posts.length">
                          <transition-group name="list" tag="ul" appear>
                                <div style="width:100%" v-for="post in posts" :key="post">
                                      <Card :post="post" @deletePost="handleDelete" />
                                </div>
                              
                          </transition-group> 
             </div>
    <div v-else class="emptyTodo">
                     THE TODO IS EMPTY
          </div>

        <h3  style="text-align : center ">Be positive</h3>


  
  </div>
</template>

<script>
// @ is an alias to /src
import Card from "@/components/card.vue";
import Toast from "@/components/toast.vue";
import { ref, provide } from "vue";

export default {
  name: "Home",
  components: { Card, Toast },

  setup(props, { emit }) {
    const posts = ref(["game","now"]);
    const input = ref("");

    const handleDelete = (post) => {
      const res = posts.value.filter((item) => {
        return item != post;
      });
      console.log(res);
      posts.value = res;
    };

    const show = ref(false);
    const addTask = () => {
    
      if (input.value.length > 0) {
        posts.value.push(input.value);
        input.value = "";
      } else {
        show.value = true;
        setTimeout(() => {
          show.value = false;
        }, 1000);
      }
    };
    return { posts, handleDelete, input, addTask, show };
  },

  mounted() {},
};
</script>

<style scoped>
* {
     box-sizing: border-box;
     padding: 0;
 
}
.emptyTodo{
  text-align: center;
  padding: 20px;
  font-family:cursive;
  font-weight: bold;
  color: orangered;
}
.container ul{
  position: relative;
  margin: 0px;
  position: relative;
}

/* list Animation */
.list-enter-from{
   transform: scale(.6);
}
.list-move{
  transition: all .3s ease;
}
.list-enter-to{
   transform: scale(1);
  
}
.list-enter-active{
    transition: all .4s ease;
}
.list-leave-active{
    transition: all .2s ease;
    position: absolute;
    
}
.list-leave-to{
transform: scale(.6);  
    
}



/* Animation */


.toast-enter-active {
  animation: wobble .5s ease;
}

/*
.trigeredToast-leave-from {
  opacity: 1;
  transform: translateY(-1px);
}
*/
.toast-leave-active {
  transition: all 1s ease;
}
.toast-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}
 @keyframes wobble {
      0% { transform: translateY(-60px); opacity: 0 }
    50% { transform: translateY(0px); opacity: 1 }
    60% { transform: translateX(8px); opacity: 1 }
    70% { transform: translateX(8px); opacity: 1 }
    80% { transform: translateX(-4px); opacity: 1 }
    90% { transform: translateX(-4px); opacity: 1 }
    100% { transform: translateX(0px); opacity: 1 }
  }
.container{
  position: relative;
}
.inputWraper {
  margin: 0px auto;
  max-width: 640px;
}
a {
  text-decoration: none;
}

 .inputWraper{
   margin-top:100px ;
 }
.input {
  outline: none;
  width: 100%;
  border: 0px;
  border-bottom: 1px solid #aaaa;
  padding: 10px;
}
</style>
