<template>
  <div>
    <TodoBar
        @clicked="processChange"
    />
      <TodoApp v-show="    place_info[0].enabled"/>
      <TodoInfo v-show="   place_info[1].enabled"/>
      <TodoContact v-show="place_info[2].enabled"/>
    </div>
</template>

<script>
import Todo from "./components/TodoApp.vue";
import TodoBar from "./components/TodoBar";
import TodoContact from "./components/TodoContact";
import TodoInfo from "./components/TodoInfo";
export default{
  components:{
    TodoApp: Todo,
    TodoBar: TodoBar,
    TodoInfo: TodoInfo,
    TodoContact: TodoContact,
  },
  methods:{
    processChange(sender){
      let index = this.place_info.findIndex(el => el.id === sender.id);
      this.place_info.forEach((item) => {item.enabled = false});
      this.place_info[index].enabled = true;
    }
  },
  data(){
    return{
      place_info: [
        {id: "app", enabled: true},
        {id: "info", enabled: false},
        {id: "contact", enabled: false},
      ]
    }
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
.main{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center ;
  padding: 50px;
}
</style>