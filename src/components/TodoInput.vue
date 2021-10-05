<template>
  <div class="input-group">
    <input type="text" v-model.trim="newTodo" v-on:keyup.enter="addNewTodo" class="form-control" placeholder="Add new To do" />
    <button v-on:click="addNewTodo" class="btn btn-outline-secondary">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
       newTodo: '',
    }
  },
  methods: {
    addNewTodo() {
      if(this.newTodo !== '') {
        this.$emit('addNewTodo', this.newTodo)

        this.newTodo = ''
      } else {
        console.log('no data')
      }
    },
  }
}
</script>

<style lang="css" scoped>
.input-group { margin-bottom: 10%; }
</style>
