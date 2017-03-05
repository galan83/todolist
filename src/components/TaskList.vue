<template>
  <ul class="task-list">
    <task-item v-for="(item, index) in items" :key="index" :task="item"></task-item>
  </ul>
</template>

<script>
import { EventBus } from '../lib/event-bus.js'
import TaskItem from './TaskItem'

export default {
  name: 'TaskList',
  components: {
    TaskItem
  },
  props: ['items'],
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
  .task-list {
    padding: 0;
  }
</style>
