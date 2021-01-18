<template>
    <table>
      <tr class = "default" :class ="[item.done ? 'finished' : 'not_finished']">
        <td @click = "dropdown" class="left_td">
          &#8627;
        </td>
        <td>
          {{item.title}}
          <div class="right-float">
            <label>
              <input type="checkbox" v-model = "item.done">
            </label>
            <button @click = "destroyElement">Delete</button>
          </div>
        </td>
      </tr>
      <tr class = "drops" v-show="item.dropped">
        <td class="borderless"></td>
        <td>Due to {{item.godz.toLocaleString()}}</td>
      </tr>
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
    }
  }
}
</script>

<style>
table{
  border-spacing: 0px;
  width: 60%;
}
.left_td{
  border: 0px;
  width: 5%;
}
.borderless{
  border: 0px;
}


</style>
