<template>
    <h2>Hello</h2>
    <ol>
        <li v-for="item in todos" v-bind:key="item.id">{{item.value}}--{{msg}}</li>
    </ol>
</template>
<script>
    export default {
        props: ["msg"],
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
