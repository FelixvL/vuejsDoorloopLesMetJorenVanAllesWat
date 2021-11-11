<template>
<hr />
    <h1>LijstComponent</h1>
    <ToDoFormComponent @vrijenaam="abc"></ToDoFormComponent>
    <h3>Alle Items:</h3>
    <ul>
        <ItemComponent 
            v-for="item in todos" 
            v-bind:key="item.id" 
            :itemtekst="item.value"
            @erisgewijzigd="hierGaanWeUpdaten"
            ></ItemComponent>
    </ul>
<hr />
</template>
<script>
    import ItemComponent from "./ItemComponent.vue";
    import ToDoFormComponent from "./ToDoFormComponent.vue";
    export default {
        components:{
            ItemComponent,
            ToDoFormComponent
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
            abc(){
                this.fetchTodos();
            },
            async hierGaanWeUpdaten(gogo){        
                const body = { value: mijnitem };
                await fetch("http://localhost:5000/todos", {
                    method: "POST",
                    headers: {
                        "content-type": "application/json",
                    },
                    body: JSON.stringify(body),
                });
            }
        },
    };

</script>

<style scoped>

</style>