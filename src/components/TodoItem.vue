<template>
    <div class="todo" v-bind:class="{completed: todo.completed}">
        <div class="d-flex align-items-center justify-content-between">
            <input type="checkbox" 
            v-bind:checked="todo.completed ? 'checked': ''"
            v-on:change="checkTodo">
            {{todo.title}}
            <button class="btn btn-danger btn-sm" @click="$emit('delete-todo', todo.id)">Eliminar</button>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        checkTodo() {
            this.todo.completed = !this.todo.completed;
        }
    },
}
</script>

<style scoped>
    .todo{
        border-bottom: solid 1px #ccc;
        padding: 10px;
    }

    .todo:not(.completed):hover{
        background-color: #eee;
    }

    .completed{
        color: #ccc;
        text-decoration: line-through;
    }

    .completed .todo-body{
        text-decoration: line-through;
    }

</style>