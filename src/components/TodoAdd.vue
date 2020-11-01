<template>
    <div class="mt-3">
        <form @submit="addTodo" class="form-group">
            <input class="form-control" placeholder="Agregar Actividad" type="text" v-model="title">
        </form>
    </div>
</template>

<script>
import { uuid } from 'vue-uuid';
export default {
    name: 'TodoAdd',
    data: () => ({
        title: ''    
    }),
    methods: {
        addTodo(e){
            e.preventDefault();

            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.title = '';
            this.$emit('add-todo', newTodo);
        }
    },
}
</script>