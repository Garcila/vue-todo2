<template>
  <div id="app" class="container">
    <h1>Stuff I Want To DO 🤡</h1>
    <input type="text" v-model="newTodo" />
    <h2>{{newTodo}}</h2>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      newTodo: ""
    };
  }
};
</script>

<style>
</style>
