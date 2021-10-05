<template>
  <div>
    <div>To Do List</div>

    <b-list-group v-if="propsTodo.length > 0">
      <div class="input-group" v-for="(todoItem,idx) in propsTodo">
        <b-list-group-item class="form-control">{{todoItem}}</b-list-group-item>
        <button v-on:click="removeTodo(todoItem,idx)" class="btn btn-outline-secondary">-</button>
      </div>
    </b-list-group>

    <div v-else>
      <div class="text-center h4">할 일을 추가해주세요.</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['propsTodo',],
  methods: {
    removeTodo(todoItem,idx) {
      // localStorage.removeItem(localStorage.key(idx));
      this.$emit('removeTodo', todoItem, idx)
    },
  },
}
</script>

<style lang="css" scoped>
</style>
