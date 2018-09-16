<template>
  <ul>
    <li v-for='item in todos' v-bind:key='item'>
      {{item}}
      <button v-on:click='del' v-bind:name='item'>done</button>
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'List',
    props: {
      todos: Array,
      remove: Function
    },
    methods: {
      del: function(e) {
        this.remove(e.target.name)
      }
    }
  }
</script>


