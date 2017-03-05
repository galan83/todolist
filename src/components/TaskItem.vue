<template>
  <li class="alert alert-success alert-dismissible task-list__item">
      <button @click="deleteTask(index)" type="button" class="close task-list__item__button">
      <span aria-hidden="true">&times;</span>
      </button><strong> {{ task.name }} </strong> {{ task.description }}
  </li>
</template>

<script>
import { EventBus } from '../lib/event-bus.js'

export default {
  name: 'TaskItem',
  props: ['task', 'index'],
  data: function () {
    return {
      taskName: '',
      taskDescription: ''
    }
  },
  methods: {
    deleteTask: function (index) {
      EventBus.$emit('delete-task', index)
    }
  }
}
</script>

<style>
  .task-list__item {
    list-style: none;
  }
</style>
