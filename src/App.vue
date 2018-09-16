<template>
  <div id="app">
    <img v-once src="./assets/logo.png" alt="Vue Logo">
    <h1 v-once>{{title}}</h1>
    <List v-bind:todos='this.todos' v-bind:remove='remove'/>
    <div class='inputBlock'>
      <input type='text' class='newItem' @change='dynamicInput'/>
      <button class='button' v-on:click='add'>&#10010;</button>
    </div>
    
  </div>
</template>

<script>
import List from './components/List.vue'

export default {
  name: 'app',
  data: function() {
    return {
      title: 'VUE TODO LIST',
      input: '',
      todos:[]
    }
  },
  components: {
    List
  },
  methods: {
    add: function() {
      this.input && this.todos.push(this.input)
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
  img {
    height: 160px;
  }
  #app {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: rgba(48, 48, 48, 0.9);
    font-style: italic;
  }
  .inputBlock {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  .newItem {
    width: 300px;
    height: 25px;
    font-size: 20px;
    color: rgba(29, 26, 26, 0.699);
    outline: rgba(48, 48, 48);
  }
  .button {
    border: none;
    background-color: transparent;
    color: rgba(48, 48, 48, 0.8);
    font-size: 20px;
    outline: none;
    cursor: pointer;
  }
</style>
