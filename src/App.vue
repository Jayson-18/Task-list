<template>
  <div id="app">
    <MyHead @add="addTask" />
    <MyContent :todos="todos" :delTask="delTask" />
    <MyFoot :todos="todos" :selectAll="selectAll" :delAllTack="delAllTack"/>
  </div>
</template>

<script>
import MyHead from "@/components/head";
import MyContent from "@/components/content";
import MyFoot from "@/components/foot";
export default {
  name: "App",
  data() {
    return {
      todos: [],
    };
  },
  created() {
    if(!JSON.parse(localStorage.getItem("todos"))){
      this.todos.push( {title: "找工作", finished: false})
    }else{
      this.todos = JSON.parse(localStorage.getItem("todos"))
    }
    console.log(this.todos)
    //this.todos = JSON.parse(localStorage.getItem("todos"));
  },
  components: {
    MyHead,
    MyContent,
    MyFoot
  },
  methods: {
    // 增加一个任务
    addTask(val) {
      this.todos.unshift({ title: val, finished: false });
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
     // 删除一个任务
    delTask(index) {
      this.todos.splice(index, 1);
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
     // 选中所有任务
    selectAll (isCheck) {
      this.todos.forEach(item => item.finished = isCheck)
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    // 清除所有任务
    delAllTack () {
      this.todos = this.todos.filter( item => !item.finished)
      localStorage.setItem("todos", JSON.stringify(this.todos));
    }
  }
};
</script>

<style>
#app {
  margin: 50px auto;
  padding: 5px 20px;
  width: 500px;
}
</style>
