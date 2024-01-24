<template>
    <div>
        <input type="text" 
                class="input" 
                placeholder=" 请输入代办事项"  
                @keyup.enter="add" 
                :class="{inputbottom:haveItems}">
    </div>
</template>

<script>
// 引入nanoid
import { nanoid } from "nanoid";
export default (await import('vue')).defineComponent({
    name: 'todoinput',
    data() {

    },
    // props:["receive"],
    props:{
        haveItems:{
            type: Boolean,
            required: true
        },
        receive:{
            type: Function,
            required: true
        }
    },
    computed: {

    },
    watch: {},
    methods: {
        add(e){
           
            // 输入值包装为对象,输入不为空
            if(e.target.value){
            const todoObj ={id:nanoid(),thing:e.target.value,done:false}
            this.receive(todoObj)
            e.target.value=""
            }
        }
    },

})
</script>
<style scoped>
.input {
    width: 50%;
    height: 36px;
    border-top-left-radius: 16px;
    border-top-right-radius: 16px;
    border: 1px solid rgb(52, 53, 65);
    margin-left: 25%;
    margin-top: 100px;
    background-color: rgb(107, 105, 105);
    font-size: 20px;
    text-indent: 0.8em;
    color: rgb(116, 253, 189);
    padding: 0px 0px;
}

.input::placeholder {
    color: #8afae0;
}
.inputbottom{
    border-bottom-left-radius: 16px;
    border-bottom-right-radius: 16px;
}
.input:focus {
    outline: black;
    box-shadow: inset 0 1.5px 1.5px rgba(158, 255, 219, 0.075), 0 0 8px rgba(103, 121, 119, 0.973)
}
</style>