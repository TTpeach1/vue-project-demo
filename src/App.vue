<template>
  <section class="todoapp">
    <!-- 除了驼峰, 还可以使用-转换链接 -->
    <TodoHeader @create='createFn'></TodoHeader>
    <TodoMain :arr='list' @del='deleteFn'></TodoMain>
    <TodoFooter></TodoFooter>
  </section>
  <!-- 第一步 注册组件 导入组件 -->
  <!-- 第二步 main接受arr数组遍历，复选框同步isDone实现选中状态，css动态绑定属性 -->
  <!-- 第三步 绑定回车事件并获取数据，自定义事件子传父， -->
  <!-- 第四步 绑定删除事件并传入当前id，自定义事件子传父，通过传入的id获取index，splice方法删除 -->
</template>

<script>
// 1.0 样式引入
import "./styles/base.css"
import "./styles/index.css"
    
import TodoHeader from "./components/TodoHeader";
import TodoMain from "./components/TodoMain";
import TodoFooter from "./components/TodoFooter";


export default {
  data(){
    return {
      list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 201, name: "睡觉", isDone: false },
        { id: 103, name: "打豆豆", isDone: true },
      ],
    }
  },
  components: {
    TodoHeader,TodoMain,TodoFooter,
  },
  methods:{
    createFn(taskName){
      let id = this.list.length==0? 100: this.list[this.list.length-1].id+1
      this.list.push({
      id,
      name: taskName,
      isDone: false,
    })
    },
    deleteFn(theid){
      const index = this.list.findIndex(obj=>obj.id == theid)
      this.list.splice(index, 1)
    }
  }
};
</script>