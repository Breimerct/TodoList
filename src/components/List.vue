<template>
  <b-list-group>
    <b-list-group-item
      v-for="(task) in tasks"
      :key="task.id"
      :variant="task.state ? 'success' : 'secondary'"
      class="d-flex justify-content-between align-items-center"
    >
      <div>
        {{ task.name }}
      </div>
      <div>
        <b-btn-group>
          <b-btn variant="danger" @click="deleteTask(task)">Delete</b-btn>
          <b-btn variant="warning" @click="editTask(task)">Edit</b-btn>
        </b-btn-group>
      </div>
    </b-list-group-item>
  </b-list-group>
</template>

<script>
export default {
  name: 'List',
  props: {
    tasks: []
  },
  methods: {
    deleteTask (task) {
      this.$emit('deleteTask', task)
    },
    editTask (task) {
      this.$emit('editTask', task)
    }
  }
}
</script>

<style scoped lang="scss">

</style>
