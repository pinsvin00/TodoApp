<template>
  <div class="modal">
    <div class="innerModal">
      <div class="stripe">
        Wprowadź date
        <div class="right-float" @click = "closeWindow">&#10006;</div>
      </div>
      <input type="datetime-local" v-model = "date">
      <button @click = addTask>Zatwierdź</button>
    </div>
  </div>
</template>

<script>
export default{
  data(){
    return{
      date: "",
    }
  },
  methods:{
    closeWindow(){
      this.$emit('close')
    },
    addTask(){
      if(this.date ===  undefined || this.date === null)
        return
      this.$emit('added', this.date)
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
  width: 30%;
  height: 10%;
}
.innerModal{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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