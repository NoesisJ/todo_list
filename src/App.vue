
<template>
  <div class='main-contain'>
    <todoinput :receive="receive" :haveItems="todos.length===0"></todoinput>

    <div class="todowrap" v-show="hasItems">

      <todoList :todos="todos" :change="change" :todoDelete="todoDelete"></todoList>

      <todoFooter :todos="todos" :allCheck="allCheck" :deleteChecked="deleteChecked"></todoFooter>

    </div>


  </div>
</template>

<script>
import todoinput from '@/components/todoInput'
import todoList from '@/components/todoList'
import todoFooter from '@/components/todoFooter'
export default (await import('vue')).defineComponent({
  components: { todoinput, todoFooter, todoList },
  data() {
    return {
      // todoList中数据
      todos:JSON.parse(localStorage.getItem("todos"))||[]

    };
  },
  computed: {
    hasItems(){
      return (this.todos.length!==0)
    }
  },
  watch: {
    todos:{
      deep:true,
      handler(value){
        localStorage.setItem("todos",JSON.stringify(value))
      }
    }
  },
  methods: {
    //接收一个todo
    receive(todoObj) {
      this.todos.unshift(todoObj)
    },
    // 改变todo中done的状态,传给item
    change(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done
      });
    },
    // 删除todo
    todoDelete(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id
      })
    },
    //全选和全不选
    allCheck(done) {
      this.todos.forEach((todo) => todo.done = done)
    },
    //删除
    deleteChecked() {
      this.todos = this.todos.filter((todo) => todo.done === false)
    }


  },
  created() {

  },
  mounted() {

  },
  beforeCreate() { }, //生命周期 - 创建之前
  beforeMount() { }, //生命周期 - 挂载之前
  beforeUpdate() { }, //生命周期 - 更新之前
  updated() { }, //生命周期 - 更新之后
  beforeDestroy() { }, //生命周期 - 销毁之前
  destroyed() { }, //生命周期 - 销毁完成
  activated() { }, //如果页面有keep-alive缓存功能，这个函数会触发
})
</script>
<style>
body {
  margin: 0;
  padding: 0;
  background: #fff;
}

.main-contain {
  width: 100%;
  height: 960px;
  background-color: rgb(68, 70, 72);
}

.todowrap {
  width: 50%;
  margin-left: 25%;
  border: 1.5px solid black;
  border-bottom-right-radius: 12px;
  border-bottom-left-radius: 12px;
  background-color: #d6d4d4;
}




</style>