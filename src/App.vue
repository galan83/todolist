<template>
  <div class="container" id="app">
    <div class="jumbotron">
      <div class="container">
        <h1>TODO list</h1>
        <p>Welcome to TODO list app</p>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-4">
        <task-form></task-form>
      </div>
      <div class="col-sm-8">
        <task-list :items="taskList"></task-list>
      </div>
    </div>
  </div>
</template>

<script>
import { EventBus } from './lib/event-bus.js'
import TaskForm from './components/TaskForm'
import TaskList from './components/TaskList'

export default {
  name: 'app',
  components: {
    TaskForm,
    TaskList
  },
  created: function () {
    EventBus.$on('delete-task', this.removeTask)
    EventBus.$on('create-task', this.createTask)
  },
  data: function () {
    return {
      taskList: [{
        name: 'Clean garage',
        description: 'Clean first floor garage.'
      }, {
        name: 'Call Paul',
        description: 'Explain Paul why the reports is not complete.'
      }]
    }
  },
  methods: {
    removeTask: function (index) {
      this.taskList.splice(index, 1)
    },
    createTask: function (task) {
      this.taskList.push(task)
    }
  }
}
</script>

<style>
  #app {
    padding: 20px 0;
  }
  .jumbotron {
    padding: 2rem;
  }
</style>
