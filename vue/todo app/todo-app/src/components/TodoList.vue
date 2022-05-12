<template>
  <div>
    <ul>
      <!-- <li v-for="todo in todos" :key=todo.index>{{ todo }}</li> -->
      <li v-for="(todo, idx) in tododata" :key="`todo-${idx}`">
        <!-- <span :class="{ completed: todo.completed }" @click="toggleTodo(todo)">{{ todo.item }}</span> -->
        <span :class="{ completed: todo.completed }" @click="toggleTodo(idx)">{{ todo.item }}</span>
        <i class="fa-solid fa-square-minus removeIcon" @click="removeTodo(todo, idx)"></i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    tododata: Array,
  },
  methods: {
    removeTodo(todo, idx) {
      this.$emit('removeTodo', todo.item, idx)

    },
    // toggleTodo(todo) {
    toggleTodo(idx) {
      // this.$emit('toggleTodo', todo)
      this.$emit('toggleTodo', idx)
    },
  }
}
</script>

<style scoped>
  li {
    display: flex;
    height: 30px;
  }

  .removeIcon {
    color:crimson;
    margin-left: auto;
  }

  .completed {
    text-decoration: line-through;
    color: gray;
  }
</style>