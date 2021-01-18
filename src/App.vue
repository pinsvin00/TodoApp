<template>
  <div>
      <h1>
        Todo
        </h1>
    <TodoApp/>
  </div>
</template>

<script>
import Todo from "./components/TodoApp.vue";
export default{
  components:{
    TodoApp: Todo
  }
}
</script>
<style>
h1{
  font-family: "DejaVu Serif";
  font-size: 48px;
  margin: 0px;
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 20px;
  background-color: indianred;
}
body{
  padding: 0;
  margin: 0;
}
</style>