<template>
    <li contenteditable @blur="eriseenverandering">{{itemtekst}}</li>
</template>
<script>
export default {
    props: ["itemtekst"],
    methods:{
        eriseenverandering(ev){
            let hoi = ev.target.innerHTML;
            this.$emit('erisgewijzigd', hoi );
        }
    },
    emits:['erisgewijzigd']
}
</script>
<style scoped>

</style>