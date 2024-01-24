<template>
        <label>
                <li>
                        <input type="checkbox" :checked="todo.done" @click="handlerChange(todo.id)" />
                        <span>&nbsp;&nbsp;{{todo.thing}}</span>
                    <button @click="handlerDelete(todo.id)">删除</button>
                </li>
        </label>
</template>

<script scoped>
export default {
    name: 'todoItem',
    data(){
        return{
            
        }
    },
    props:["todo","change","todoDelete"],
    methods:{
        // 处理勾选的gaib
        handlerChange(id){
            this.change(id)
        },
        //处理shanc
        handlerDelete(id){
            if(confirm("确认删除吗？"))
            this.todoDelete(id)
        }
    }
}
    
</script>

<style scoped>
input {
    width: 16px;
    height: 16px;
}

li {
    list-style: none;
    height: 42px;
    line-height: 42px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
}

li label {
    float: left;
    cursor: pointer;
}

li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
}

li:hover{
    background-color: rgb(185, 181, 181);
    cursor: pointer;
}

li:hover button{
    display: block;
}

button {
    float: right;
    display: none;
    margin-top: 8px;
    width: 68px;
    height: 28px;
    border-radius: 8px;
}
button:hover{
    background-color: rgb(157, 255, 234);
    cursor: pointer;
}

li:before {
    content: initial;
}

li:last-child {
    border-bottom: none;
}</style>

