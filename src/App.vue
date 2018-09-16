<template>
  <div id="app">
    <h1 v-once>{{title}}</h1>
    <List v-bind:todos='this.todos' v-bind:remove='remove'/>
    <input @change='dynamicInput'/>
    <button v-on:click='add'>add</button>
  </div>
</template>

<script>
import List from './components/List.vue'

export default {
  name: 'app',
  data: function() {
    return {
      title: 'TODO LIST',
      input: '',
      todos:[]
    }
  },
  components: {
    List
  },
  methods: {
    add: function() {
      this.todos.push(this.input)
    },
    dynamicInput: function(e) {
      this.input = e.target.value
      e.target.value = ''
    },
    remove: function(item) {
      this.todos = this.todos.filter(el=> el!==item)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-style: italic;
  margin-top: 60px;
}
</style>
