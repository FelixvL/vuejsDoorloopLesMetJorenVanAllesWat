<template>
    <h4>oei</h4>
    <form v-on:submit="voegToDoItemToe">
    <label>
      ToDo Item
      <input name=voornaam type="text" />
    </label>
    <button>Maak Nieuw</button>
  </form>
</template>
<script>
export default {
    methods:{
        voegToDoItemToe(eve){
            eve.preventDefault();
            let tditem = eve.target.elements.voornaam.value;
            console.log(tditem); 
            this.addTodo(tditem);
        },
        async addTodo(mijnitem) {
            const body = { value: mijnitem };
            await fetch("http://localhost:5000/todos", {
                method: "POST",
                headers: {
                    "content-type": "application/json",
                },
                body: JSON.stringify(body),
            });
            //this.$parent.abc();
            this.$emit('vrijenaam')
        },

    },
    emits: ['vrijenaam']
}
</script>
<style scoped>

</style>