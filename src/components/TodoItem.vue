<template>
  <div class="container">
    <span
      class="todo-item"
      :class="{'finished': todo.status === 'finished'}"
    >
      {{ todo.name }}
    </span>

    <div class="btn btn-outline-primary click" @click="handleRemove(todo.id)">
      delete
    </div>

    <div class="btn btn-outline-primary click" @click="handleUpdate(todo.id)">
      update
    </div>

    <div
      class="btn btn-success click btn-stt"
      @click="handleChangeStt(todo.id)"

    >
      {{ todo.status }}
    </div>

    <!-- <td>
            <span :class="{ 'line-through': todo.status === 'finished' }">
              {{ todo.name }}
            </span>
          </td>
          <td>
            <span
              class="pointer noselect"
              @click="changeStatus(index)"
              :class="{
                'text-danger': todo.status === 'to-do',
                'text-success': todo.status === 'finished',
               
              }"
            >
              {{ capitalizeFirstChar(todo.status) }}
            </span>
          </td>
          <td class="text-center">
            <div class="click" @click="deleteTask(index)">del</div>
          </td>
          <td class="text-center">
            <div class="click" @click="editTask(index)">edit</div>
          </td> -->
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  components: {},

  data() {
    return {};
  },

  name: "todo-item",

  methods: {
    handleRemove(value) {
      this.$emit("willDelete", value);
    },

    handleChangeStt(value) {
      this.$emit("willChangeStt", value);
    },

    handleUpdate(value) {
      this.$emit("willUpdate", value);
    },
  },
};
</script>

<style>
.todo-item {
  float: left;
  width: 70%;
}

.btn-stt {
  width: 80px;
}

.click {
  vertical-align: middle;
  float: right;
  margin-right: 5px;
}

.finished{
  text-decoration: line-through;
}
</style>
