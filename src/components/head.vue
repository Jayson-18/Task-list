<template>
  <div class="head-wrapper">
    <input class="text" type="text" placeholder="请输入任务，按回车键确认" @keyup.enter="push" v-model="val">
  </div>
</template>
  
<script>
export default {
  data () {
    return {
      val:'',
    }
  },
  methods: {
    push (e) {
    if(!this.val.trim()){
      alert('添加的信息不能为空哦')
      return;
    }
      this.$emit('add', this.val)
      this.val = '';
    }
  }
}
</script>

<style scoped>
  .head-wrapper{
    width: 100%;
  }
  .head-wrapper .text{
    width: 100%;
    height: 30px;
    line-height: 30px;
    font-size: 16px;
    border-radius: 5px;
    outline: none;
    border: 1px solid rgb(194, 194, 194);
    text-indent: 8px;
  }
  .head-wrapper .text:focus{
    border-color: rgb(238, 201, 176);
  }
  .head-wrapper .text::placeholder{
    color: rgba(0, 0, 0, .2)
  }
</style>
