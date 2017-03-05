<template>
  <form @submit.prevent class="task-form">
    <div class="form-group task-form__name">
      <label for="taskName" class="task-form__name__label">Task name</label>
      <input v-model="taskName" type="text" class="form-control task-form__name__input" id="taskName" placeholder="Name">
   </div>
   <div class="form-group task-form__description">
     <label for="taskDescription" class="task-form__description__label">Task description</label>
     <input v-model="taskDescription" type="text" class="form-control task-form__description__input" id="taskDescription" placeholder="Description">
   </div>
   <button @click="createTask" class="btn btn-primary search-form__button">Create task</button>
 </form>
</template>

<script>
import { EventBus } from '../lib/event-bus.js'

export default {
  name: 'TaskForm',
  data: function () {
    return {
      taskName: '',
      taskDescription: ''
    }
  },
  methods: {
    createTask: function () {
      if (this.taskName !== '') {
        EventBus.$emit('create-task', {'name': this.taskName, 'description': this.taskDescription})
        this.taskName = ''
        this.taskDescription = ''
      }
    }
  }
}
</script>

<style>
</style>
