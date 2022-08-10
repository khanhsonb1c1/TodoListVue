
<template>
  <div class="container h3">

    <TodoList></TodoList>


  </div>
</template>


<script>
import TodoList from "./components/TodoList.vue";


export default {
  components: {
    TodoList,
    
},

  methods: {},

  data() {
    return {
     
    };
  },
};
</script>



<style>
* {
  box-sizing: border-box;
}



#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}
</style>
