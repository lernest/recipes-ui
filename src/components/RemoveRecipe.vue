<template>
    <div>
        <h2>Remove Recipe</h2>
        <div class="input-row">
                <label>Recipe to remove:</label>
                <input type="text" v-model="recipe">
            </div>
            <button @click="removeRecipe">Remove</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            recipe: ""
        }
    },
    methods:{
        removeRecipe(){
            const request = {
                recipe: this.recipe
            }
            console.log('removing recipe')
            console.log(request)
            this.$emit('removeRecipe',request)
        }
    }
}
</script>

<style>

</style>