<template>
  <div class="text-center">
    <button type="button" v-on:click="removeTodoAll" class="btn btn-sm btn-outline-danger">Clear All</button>
  </div>
</template>

<script>
export default {
  methods: {
    removeTodoAll() {
      this.$emit('removeTodoAll')
    },
  }
}
</script>

<style lang="css" scoped>
</style>
