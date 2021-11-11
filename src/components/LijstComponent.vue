<template>
    <h1>LijstComponent</h1>
    <ul>
        <ItemComponent v-for="item in todos" v-bind:key="item.id" :msg="item.value"></ItemComponent>
    </ul>
</template>
<script>
    import ItemComponent from "./ItemComponent.vue";
    export default {
        components:{
            ItemComponent
        },
        data(){
            return {
                todos: [],
            };
        },
        mounted(){
            this.fetchTodos();
        },
        methods:{
            async fetchTodos(){
                const response = await fetch("http://localhost:5000/todos");
                const result = await response.json();
                this.todos = result;
            },
        },
    };

</script>

<style scoped>

</style>