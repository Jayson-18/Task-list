<template>
  <div class="content-box">
    <ul class="content">
      <Myli v-for="(item, index) in todos" :key="index" :todo="item" :index="index" :delTask="delTask"/>
      <!-- <li v-for="(item, index) in todos" 
          :key="index" 
          :style="{backgroundColor:bgColor}"
          @mouseenter="show(index)"
          ref="li" >
        <label>
          <input type="checkbox" :checked="item.finished"/>
          {{item.title}}
        </label>
        <button v-show="flag">删除</button>
      </li> -->
    </ul>
  </div>
</template>

<script>
import Myli from '@/components/item'
export default {
  data() {
    return {
      bgColor:'#fff',
      flag:false,
    };
  },
  props: ['todos','delTask'],
  components:{
    Myli
  },
  methods: {
    show (index) {
      // this.$refs.li.forEach(ele => ele.classList.remove('active'))
      // this.$refs.li[index].classList.add('active')
      // console.log(index);
      // this.bgColor = "#fcf5e3";
    }
  }
};
</script>

<style scoped>
.content-box {
  width: 100%;
}
.content-box .content {
  margin: 0;
  padding: 0;
}
.content-box .content li {
  position: relative;
  margin-top: 10px;
  padding: 5px 0px;
  height: 30px;
  box-shadow: 0 1px 2px 0 rgba(0,0,0,.08);
  overflow: hidden;
  line-height: 30px;
  list-style-type: none;
  user-select: none;
}
.content-box .content li:first-of-type {
  margin-top: 20px;
}

</style>