<template>
  <div class="modal">
    <div class="innerModal">
      <div class="stripe">
        Wprowadź date
        <div class="right-float" @click = "closeWindow">&#10006;</div>
      </div>
      <input type="datetime-local" v-model = "date">
      <input type="text" placeholder="Opis wydarzenia" v-model="descp">
      <button @click = addTask>Zatwierdź</button>
    </div>
  </div>
</template>

<script>
export default{
  data(){
    return{
      date: "",
      descp: "",
    }
  },
  methods:{
    closeWindow(){
      this.$emit('close')
    },
    addTask(){
      if(this.date ===  undefined || this.date === null)
        return
      this.$emit('added', this)
    }
  }
}
</script>

<style>
.modal{
  background-color: ghostwhite;
  border: solid 1px black;
  position: absolute;
  float: left;
  width: 40%;
  height: 20%;
}
.innerModal{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.innerModal > input{
  margin: 5px;
}

.stripe{
  background-color: green;
  font-size: 18px;
  text-align: center;
  font-family:"Bahnschrift";
  width: 100%;
}
.right-float{
  float:right;
}
</style>