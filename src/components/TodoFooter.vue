<template>
  <footer class="footer">
    <span class="todo-count">剩余<strong>{{count}}</strong></span>
    <ul class="filters" >
      <li>
        <a :class="{selected:isAll='all'}" href="javascript:;" @click="change('all')">全部</a>
      </li>
      <li>
        <a :class="{selected:isAll='no'}" href="javascript:;" @click="change('no')">未完成</a>
      </li>
      <li>
        <a :class="{selected:isAll='yes'}" href="javascript:;" @click="change('yes')">已完成</a>
      </li>
    </ul>
    <button class="clear-completed" @click='delAll'>清除已完成</button>
  </footer>
</template>

<script>
export default {
  data(){
    return{
      isAll:'',
    }
  },
  props:['count'],
  methods:{
    change(val){
      this.isAll=val;
      console.log(val);
      this.$emit('filterAll',val);
    },
    delAll(){
      this.$emit('clear');
    }
  }
}
</script>