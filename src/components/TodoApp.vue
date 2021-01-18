

<template>
  <div class = "main">
    <TodoModalDate
        v-show="dateInput"
        @close="close_modal"
        @added="add_activity"
    />
      <TodoItem
          v-for="item in items"
          :key="item.id"
          :item = "item"
          @removeClicked="remove_item"
          @dropped = "drop_item"
      />
    <p>{{input}}</p>
    <h2>Nazwa wydarzenia</h2>
    <input type="text" placeholder="Nazwa wydarzenia" v-model = "input">
    <button @click = "date_modal">Wprowadź</button>
  </div>
</template>

<script>
import TodoItem from './TodoItem'
import TodoModalDate from "@/components/TodoModalDate";
export default {


  components:{
    TodoItem,
    TodoModalDate
  },


  data(){
    return{
      input: "",
      dateInput: false,
      items: [
      ]
    }
  },


  mounted(){
    if(localStorage.input){
      this.input = localStorage.input;
    }
    if(localStorage.items){
      console.log(localStorage.items);
      this.items = JSON.parse(localStorage.items)
    }
  },


  methods: {
    greet(){
      alert("Hello world!")
    },
    date_modal(){
      this.dateInput = true
    },
    close_modal(){
      this.dateInput = false
    },
    add_activity(date){
      let last_id;
      if(this.items.length === 0){
        last_id = 0;
      } else last_id = this.items[this.items.length-1].id;

      this.items.push({title: this.input, godz:date, id: last_id+1, dropped:false});
      this.input = "";
      this.dateInput = false
    },
    remove_item(item){
      const index = this.items.findIndex(el => el.id === item.id)
      this.items.splice(index, 1)
    },
    drop_item(item){
      const index = this.items.findIndex(el => el.id === item.id);
      this.items[index].dropped = !this.items[index].dropped;
      console.log(this.items[index].dropped)
    }
  },


  watch:{
    input(newInput){
      localStorage.input = newInput;
    },
    items(newItems){
      localStorage.items = JSON.stringify(newItems);
    }
  }
}
</script>

<style>
.finished{
  font-family: "Bahnschrift";
  font-size: 24px;
  color: green;
}
.not_finished{
  font-size: 24px;
  font-family: "Bahnschrift";
}
.main{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center ;
}
.tasks{
  border-spacing: 0px;
  width: 50%;
}
</style>
