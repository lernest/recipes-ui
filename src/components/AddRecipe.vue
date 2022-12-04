<template>
    <div>
        <h2>Add Recipe</h2>
        <div class="inputs flex-column">
            <div class="input-row">
                <label>Recipe:</label>
                <input type="text" v-model="recipe">
            </div>
            <div class="input-row">
                <label>Ingredients:</label>
                <input type="text" v-model="ingredients">
            </div>
            <div class="input-row">
                <label>Directions:</label>
                <input type="text" v-model="directions">
            </div>
        </div>
        <button @click="submitRecipe"> Submit </button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            recipe: "",
            ingredients: "",
            directions: ""
        }
    },
    methods:{
        submitRecipe(){
            const request = {
                recipe: this.recipe,
                ingredients: this.ingredients,
                directions: this.directions
            }
            console.log('recipe submitted')
            console.log(request)
            this.$emit('addRecipe',request)
        }
    }
}
</script>

<style>

</style>