<template>
    <div class="container">
        <input type="text" placeholder="Buscar Actividad" class="form-control" v-model="query" v-on:input="$emit('query-change', query)">
    </div>
</template>

<script>
export default {
    name: 'Search',
    data: () => ({
        query: ''
    }),
}
</script>