<template>
  <h1>{{title}}</h1>
  <form v-on:submit="bijSubmit">
    <label>
      Voornaam
      <input name=voornaam type="text" />
    </label>
    <button>Submit</button>
  </form>
  {{voornaam}}
  <span @click="hoi">hallo allemaal</span>
    <HelloWorld msg="planet"></HelloWorld>
    <LijstComponent></LijstComponent>
</template>

<style scoped>
  h1{
    color:orange;
  }
</style>
<script>
  import HelloWorld from "./components/HelloWorld.vue";
  import LijstComponent from "./components/LijstComponent.vue";
  
  export default {
    components:{
      HelloWorld,
      LijstComponent
    },
    data(){
      return{
        voornaam : "", 
        title: "hoi daar",
      }
    },
    created(){
      this.voornaam = "gaan";
    },
    methods:{
      bijSubmit(evenement){
        evenement.preventDefault();
        console.log(evenement.target.elements.voornaam.value);
        this.voornaam = evenement.target.elements.voornaam.value;
      },
      hoi(eve){
        console.log(eve);
      }
    }
  };
</script>
