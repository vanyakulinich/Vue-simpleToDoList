<template>
  <ul class='list'>
    <li class='item' v-for='item in todos' v-bind:key='item'>
      {{item}}
      <button class='button' v-on:click='del' v-bind:name='item'>&#10004;</button>
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

<style scoped>
  .list {
    list-style-type: none;
    padding: 0;
    width: 60%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .item {
    width: 90%;
    display: flex;
    margin: 5px 0;
    font-size: 20px;
    font-style: italic;
    color: rgba(48, 48, 48, 0.6);
    position: relative;
  }
  .button {
    color: green;
    position: absolute;
    right: 0;
  }
</style>



