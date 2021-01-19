<template>
  <div class = "bar">
    <h1>TodoApp</h1>
    <h3 @click="move"><a id="app">Strona główna</a></h3>
    <h3 @click="move"><a id="info" >Dodatkowe informacje</a></h3>
    <h3 @click="move"><a  id="contact">Kontakt</a></h3>
  </div>
</template>

<script>
export default {
name: "TodoBar",
  methods:{
    move(e){
      this.$emit('clicked', e.target)
    }
  },
  data(){
    return{

    }
  }
}



</script>

<style scoped>
  .bar{
    width: 100%;
    display:flex;
    background-color: indianred;
    align-items: center;
    flex-direction: row;
  }
  h1{
    margin-right: 30px;
  }
  h3{
    margin-right: 30px;
    cursor: default;
  }
  a{
    cursor:default;
  }
  h3 > a {
    position: relative;
    color: #000;
    text-decoration: none;
  }

  h3 > a:hover {
    color: #000;
  }
  h3 > a::before {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    bottom: 0;
    left: 0;
    background-color: #000;
    visibility: hidden;
    transform: scaleX(0);
    transition: all 0.3s ease-in-out 0s;
  }
  h3 > a:hover::before {
    visibility: visible;
    transform: scaleX(1);
  }
</style>