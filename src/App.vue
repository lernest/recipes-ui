<template>
  <div id="app">
    <div class="flex-container">

      <div class="flex-item">
        <AddRecipe v-on:addRecipe="addRecipe"/>
        <code>
          {{addResponse}}
        </code>
      </div>
      <div class="flex-item">
        <ListRecipes v-on:listRecipes="listRecipes"/>
        <code>{{listResponse}}</code>
      </div>
      <div class="flex-item">
        <RemoveRecipe v-on:removeRecipe="removeRecipe"/>
        <code>{{removeResponse}}</code>
      </div>
    </div>
      <div>Health check: {{healthCheck}}</div>
  </div>
</template>

<script>
import axios from 'axios'
import AddRecipe from './components/AddRecipe.vue'
import RemoveRecipe from './components/RemoveRecipe.vue'
import ListRecipes from './components/ListRecipes.vue'

export default {
  name: 'App',
  components: {
    AddRecipe,
    ListRecipes,
    RemoveRecipe
  },
  data(){
    return{
      healthCheck: null,
      rows: [],
      addResponse: "",
      listResponse:"",
      removeResponse:""
    }
  },
  mounted(){
    axios.get('http://localhost:3000/')
      .then(response => (this.healthCheck = response.status))
  },
  methods:{
    addRecipe(request){
      console.log(request)
      axios.post('http://localhost:3000/add',request)
      .then(response => (this.addResponse = response))
    },
    listRecipes(){
      axios.get('http://localhost:3000/recipes')
      .then(response => this.listResponse = response)
    },
    removeRecipe(request){
      console.log("app removing recipe")
      console.log(request)
      axios.post('http://localhost:3000/remove',request)
      .then(response => this.removeResponse = response)
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.flex-container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 30px;
}

.flex-item{
  border: 1px solid black;
  margin: 0 auto;
  padding: 10px 40px;
  flex-basis: 30%;
  height: 600px;
  overflow: scroll;
}

.flex-column{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.input-row{
  margin: 10px 5px;
}

input{
  margin-left: 5px;
}

button{
  padding: 10px;
  border-radius: 5px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>``
