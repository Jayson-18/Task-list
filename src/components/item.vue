<template>
  <li @mouseenter="dealShow"  @mouseleave="dealHide" :style="{backgroundColor:bgColor}">
    <label>
      <input type="checkbox" :checked="todo.finished" @click="changeStatus"/>
      {{todo.title}}
    </label>
    <button v-show="isShow" @click.stop="remove">删除</button>
    <button v-show="isShow" :class="{active:flag}" @click="isRemove">确认删除</button>
  </li>
</template>

<script>
export default {
  data () {
    return{
      bgColor: '#f8f8f8',
      isShow: false,
      flag:false,
    }
  },
  props: ["todo", 'index', 'delTask'],
  methods: {

    // 鼠标yiru 显示按钮隐藏 改变bg
    dealShow () {
      this.bgColor = '#f8edce'
      this.isShow = true;
    },

    // 鼠标移出 删除按钮隐藏 确认删除按钮去掉class 改变bg
    dealHide () {
      this.isShow = false;
      this.flag = false;
      this.bgColor = '#f8f8f8'
    },
    // 改变完成任务
    changeStatus () {
      this.todo.finished = !this.todo.finished;
    },
    // 删除任务
    remove () {
      this.flag = true;
      localStorage.setItem("todos", JSON.stringify(this.todo))
    },
    // 确认删除任务
    isRemove () {
      this.flag = false;
      this.delTask(this.index);
    }
  }
};
</script>

<style scoped>
li button {
  position: absolute;
  top: calc(50% - 14px);
  right: 4px;
  padding: 0px 12px;
  height: 28px;
  line-height: 28px;
  border: none;
  border-radius: 2px;
  color: #fff;
  background-color: rgb(231, 29, 29);
  outline: none;
  cursor: pointer;
}
li button:nth-of-type(2){
  top: 0px;
  right: -78px;
  height: 40px;
  line-height: 40px;
}
li button:nth-of-type(2).active{
  right: 4px;
  transition: all .2s ease-out;
}
</style>