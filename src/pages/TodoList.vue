<template>
  <b-container>
    <h1 class="mt-3 text-center">ToDoList</h1>
    <div class="mt-3">
      <b-input-group
        size="lg"
        class="mb-3"
      >
        <b-form-input v-model="taskName" @keypress.enter="saveTask"></b-form-input>
        <b-input-group-append>
          <b-button size="lg" text="Button" variant="success" @click="saveTask">SAVE
          </b-button>
        </b-input-group-append>
      </b-input-group>
    </div>
    <list :tasks="tasks" @deleteTask="deleteTask" @editTask="editTask"/>
  </b-container>
</template>

<script>
import List from '../components/List'
export default {
  name: 'TodoList',
  components: { List },
  data: () => ({
    taskName: '',
    tasks: []
  }),
  methods: {
    saveTask () {
      if (this.taskName === '') {
        return
      }
      this.tasks.push({
        id: Date.now(),
        name: this.taskName,
        state: false
      })
      this.taskName = ''
    },
    deleteTask (task) {
      if (!confirm('¿are you sure?')) {
        return
      }
      const index = this.tasks.indexOf(task)
      this.tasks.splice(index, 1)
    },
    editTask (task) {
      const taskEdit = this.tasks.find(t => t.id === task.id)
      taskEdit.state = true
    }
  }
}
</script>

<style scoped lang="scss">

</style>
