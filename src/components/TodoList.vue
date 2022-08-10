<template>
  <div class="container" style="max-width: 1000px">
    <h2 class="text-center mt-5">Todo App</h2>

    <!-- Input -->
    <div class="d-flex mt-5">
      <input
        type="text"
        v-model="todo"
        placeholder="Enter task"
        class="w-100 form-control"
      />
      <button class="btn btn-warning rounded-0" @click="submitTask">
        SUBMIT
      </button>
    </div>

    <ul class="list-group">
      <li v-for="todo in todos" :key="todo.id" class="list-group-item list-group-item-secondary">
        <TodoItem :todo="todo"
        @willDelete="deleteTask"
        @willUpdate="editTask"
        @willChangeStt="changeStatus"
        ></TodoItem>
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";


export default {
  props: {
    msg: String,
  },
  data() {
    return {
      todo: "",
      editedTask: null,
      statuses: ["to-do","finished"],

      todos: [
        {
          id: 1,
          name: "action 1",
          status: "to-do",
        },
        {
          id: 2,
          name: "action 2",
          status: "to-do",
        },
        {
          id: 3,
          name: "action 3",
          status: "finished",
        },
      ],
    };
  },
  methods: {
   
    // capitalizeFirstChar(str) {
    //   return str.charAt(0).toUpperCase() + str.slice(1);
    // },
    
    changeStatus(value) {
      let newIndex = this.statuses.indexOf(this.todos[value-1].status);
      if (++newIndex > 1) newIndex = 0;
      this.todos[value-1].status = this.statuses[newIndex];
    },
   
    deleteTask(value) {
      this.todos.splice(value-1, 1);
    },
    
    editTask(value) {
      this.todo = this.todos[value-1].name;
      this.editedTask = value-1;
    },
    
    submitTask() {
      if (this.todo.length === 0) return;
      /* We need to update the task */
      if (this.editedTask != null) {
        this.todos[this.editedTask].name = this.todo;
        this.editedTask = null;
      } else {
        /* We need to add new task */
        this.todos.push({
          name: this.todo,
          status: "todo",
        });
      }
      this.todo = "";
    },
  },
  components: { TodoItem },
};
</script>

<style scoped>
* {
  font-size: 18px;
}
li{
  margin-top: 10px;
}

.w-100 {
    margin-right: 20px;
}


.click {
  font-size: 12px;
  height: 20px;
  width: 30px;
  background-color: red;
  border-radius: 5px;
}
.pointer {
  cursor: pointer;
}
.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}
.line-through {
  text-decoration: line-through;
}
</style>
