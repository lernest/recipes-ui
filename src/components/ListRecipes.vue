<template>
    <div>

        <h2>List recipes</h2>
        <button @click="listRecipes"> Get Recipes </button>
    </div>
</template>

<script>
export default {
    methods:{
        listRecipes(){
            console.log("list recipe button click")
            this.$emit('listRecipes')
        }
    }
}
</script>

<style>

</style>