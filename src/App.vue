<template>
  <div id="app">
    <todo-list/>
  </div>
</template>

<script>

import TodoList from './pages/TodoList'
export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style lang="scss" scoped>
</style>
