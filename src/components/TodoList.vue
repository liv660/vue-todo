<template>
  <div>
    <div>To Do List</div>
    <div v-if="propsTodo.length > 0">
      <b-list-group>
        <div class="input-group" v-for="(todoItem,idx) in propsTodo">
          <b-list-group-item class="form-control">{{todoItem}}</b-list-group-item>
          <button v-on:click="removeTodo(todoItem,idx)" class="btn btn-outline-secondary">-</button>
        </div>
      </b-list-group>
      <TodoDeleteAll v-on:removeTodoAll="removeTodoAll"/>
    </div>

    <div v-else>
      <div class="text-center h4">할 일을 추가해주세요.</div>
    </div>
  </div>
</template>

<script>
import TodoDeleteAll from './TodoDeleteAll.vue'

export default {
  props: ['propsTodo',],
  components: {
    TodoDeleteAll,
  },
  methods: {
    removeTodo(todoItem,idx) {
      this.$emit('removeTodo', todoItem, idx)
    },
    removeTodoAll() {
      this.$emit('removeTodoAll')
    },
  },
}
</script>

<style lang="css" scoped>
.list-group {margin-bottom: 5%;}
</style>
