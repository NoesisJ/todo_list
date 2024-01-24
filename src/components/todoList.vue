<template>
    <ul class="todo-main">
        <todoItem v-for="todoObj in todos" 
                :key="todoObj.id" 
                :todo="todoObj"
                :change="change"
                :todoDelete="todoDelete"
                ></todoItem>
    </ul>
</template>

<script>

import todoItem from '@/components/todoItems'
export default (await import('vue')).defineComponent({
    name: 'todoList',
    components: { todoItem },
    data() {},
    props:["todos","change","todoDelete"],
})
</script>
<style lang='scss' scoped>
//@import url(); 引入公共css类
.todo-main {
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
}

.todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
}
</style>