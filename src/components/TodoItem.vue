<template>
    <table>
      <tr class = "default" :class ="[item.done ? 'finished' : 'not_finished']">
        <td @click="dropdown">
            {{item.title}}
        </td>
      <td>
          <div class="right-float">
            <label>
              <input type="checkbox" v-model = "item.done">
            </label>
            <button @click = "destroyElement">Delete</button>
          </div>
        </td>
      </tr>
      <div class = "drops" v-show="item.dropped">
        <tr class="description">
          <td>{{item.description}}</td>
        </tr>
        <tr>
          <td>{{pretty_date}}</td>
        </tr>
      </div>

    </table>
</template>



<script>
export default{
  props: ['item'],
  methods:{
    destroyElement(){
      this.$emit('removeClicked', this.item.id)
    },
    dropdown(){
      this.$emit('dropped', this.item)
    },

  },
  computed:{
    pretty_date(arg){
      if(arg.item.godz === ""){
        return "Nieokreslono";
      }
      let a = arg.item.godz;
      let date_time = a.split('T');
      let date = date_time[0];
      let time = date_time[1];
      return "Do " + date + " " + time;
    }
  }
}
</script>

<style>
table{
  border-spacing: 0px;
  width: 60%;
}
.description{
  font-size: 24px;

}
.left_td{
  border: 0px;
  width: 5%;
}
.borderless{
  border: 0px;
}
.drops{
  margin-left: 10%;
}

td{
  cursor: default;
}


</style>
