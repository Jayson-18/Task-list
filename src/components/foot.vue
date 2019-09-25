<template>
  <div class="foot-box">
    <input type="checkbox"  v-model="isChecked">
    <span>已完成{{select}}件/</span>
    <span>总计{{todos.length}}件</span>
    <button class="remove" @click="del">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  props:['todos', 'selectAll', 'delAllTack'],
  computed:{
    select () {
      if(this.todos.length != 0){
        return this.todos.reduce((total, todo)=> total + (todo.finished ? 1 : 0), 0)
      }else{
        return 0;
      }
    },
    isChecked: {
      get () {
        return this.select === this.todos.length && this.todos.length > 0;
      },
      set (val) {
        this.selectAll(val);
      }
    }
  },
  methods: {
    del () {
      this.delAllTack();
    }
  }

}
</script>

<style scoped>
  .foot-box{
    position: relative;
    margin-top: 30px;
    height: 40px;
    line-height: 40px;
  }
  .foot-box .remove{
    position: absolute;
    right: 4px;
    top: calc(50% - 17px);
    padding: 0px 15px;
    height: 34px;
    line-height: 34px;
    font-size: 16px;
    color: #fff;
    border: none;
    border-radius: 5px;
    background-color: rgb(236, 172, 34);
    outline: none;
    cursor: pointer;
  }

  .remove:hover{
    transition: all .3s ease-in;
    background-color:rgb(231, 29, 29);
  }
</style>
  
