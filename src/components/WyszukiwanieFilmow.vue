<template>
  <div>
    <h1>Baza fimów</h1>
    <form>
      <div v-for="keys,index in mov" :key="keys.Object" >
      <div v-if="keys!='year'">
        <label>{{keys}} : </label>
        <input v-model="attr[index]"/>
      </div>
      <div v-else>
        <label>Form {{keys}} : </label>
        <input type="number" min="1900" v-model="attr[index]"/>
        <label>To {{keys}} : </label>
        <input type="number" min="1900" max="2022" v-model="attr[index+3]"/>
      </div>
    </div>
    <button @click.prevent="submited()">Szukaj</button>
  </form>
    
  </div>
</template>

<script>
import movies from "E:/VueProject/hello-world/wikipedia-movie-data-master/wikipedia-movie-data-master/movies.json"
export default {
  data(){
    return{
      mov : Object.keys(movies[0]),
      attr : [],
      value : []
    }
  },
  methods:{
    submited() {
      this.value = this.attr.slice()
      this.$emit('submit',this.value)
    }
  },
}
</script>
