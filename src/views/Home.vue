<template>
 
  <div>
     <input 
     class="input" type="text" placeholder="Enter to add task " @keypress.enter="addTask"
     v-model="input"
     >

    <div v-for="post in posts" :key="post">
      <Card :post="post" @deletePost="handleDelete" />
    </div>
 
  </div>
  
</template>

<script>
// @ is an alias to /src
import Card from '@/components/card.vue'
import { ref ,provide} from 'vue'

export default {
  name: 'Home',
  components: {Card},


  setup(props,{emit}){

    const  posts = ref([])
    const input =ref("")

    const handleDelete =(post)=>{
       const res = posts.value.filter((item)=>{
          return  item !=post

        })
        console.log(res)
         posts.value = res;
        
        };

 const addTask =()=>{
      posts.value.push(input.value)
      input.value=""

 }  
    return {posts, handleDelete,input,addTask}
  },

  mounted() {
   
 
}
}
</script>

<style scoped>
*{
box-sizing: border-box;
}
a{
  text-decoration: none;
}
.input{
  outline:none;
  width:100%;
  border: 0px;
  border-bottom: 1px solid #aaaa;
 padding: 10px;
}

</style>
