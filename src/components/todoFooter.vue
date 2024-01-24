<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" class="footer-input" 
                        :checked="doneAll==todos.length" 
                        @change="checkAll">
        </label>
        <span>
            <span >已完成{{doneAll}}个
            </span>/共{{ todos.length }}个
        </span>
        <button @click="allDelete">清除已完成任务</button>
    </div>
</template>

<script>

export default (await import('vue')).defineComponent({
    name: 'todoFooter',
    components: {},
    data() {
        return {
            hasItem:false
        };
    },
    props:["todos","allCheck","deleteChecked"],
    computed: {
        doneAll(){
            return this.todos.filter((todo)=>todo.done===true).length
        },
    },
    watch: {},
    methods: {
        checkAll(e){
            this.allCheck(e.target.checked)
        },
        allDelete(){
            if(confirm("确定删除选定内容吗？"))
            this.deleteChecked()
        }
    },
    created() {

    },
    mounted() {

    },

})
</script>
<style lang='scss' scoped>
.todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 3px;
}

.todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
}

.todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
}

.todo-footer button {
    float: right;
    margin-top: 3px;
}

.footer-input{
    width: 20px;
    height: 20px;
}
.footer-input:hover{
    cursor: pointer;
}
button{
    border-radius: 8px;
    box-shadow: 1px black;
    margin-right: 3px;
    height: 27.5px;
}
button:hover{
    background-color: rgb(157, 255, 234);
    cursor: pointer;
}
</style>