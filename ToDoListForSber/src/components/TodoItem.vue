<template>
    <div :class="[
            'todo-item',
            { 'is-complete': todo.completed }
        ]"
    >
        <p>
            <input class="check" type="checkbox" @change="markComplete">
            {{ todo.title }}
             <button class="del" @click="$emit('delItem', todo.title)">x</button>
        </p>
    </div>
</template>

<script>
    export default  {
        name: 'TodoItem',
        props: {
            todo: {
                type: Object
            }
        },
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    
    .todo-item {
        max-width: 500px;
        width: 100%;
        min-height: 40px;
        margin: 10px auto;
        background: #ffffff;
        padding: 10px;
        box-shadow: 0 0 10px 0 rgb(224, 224, 224);
        border-radius: 15px;
        white-space: wrap;
    }

    .check{
        width: 15px;
        height: 15px;
        margin: 4px 0 0 0;
    }
    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #c72e2e;
        color: #fff;
        border: none;
        padding: 3px 9px 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
        font-size: 13px;
    }
    
</style>