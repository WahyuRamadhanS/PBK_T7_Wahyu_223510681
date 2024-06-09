  <!-- src/App.vue -->
  <template>
    <div id="app">
      <TodoList />
    </div>
  </template>

  <script>
  import TodoList from './components/TodoList.vue';

  export default {
    components: {
      TodoList,
    },
  };
  </script>

  <style scoped>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
  }
  </style>
