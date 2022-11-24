<template>
  <div>
    <h1>Baza fimów</h1>
    <form>
      <div v-for="(keys,index) in mov" :key="keys.Object" >
        <div class="input-group mb-3" v-if="keys!='year'">
          <label class="input-group-text" :style="'text-transform: capitalize;'">{{keys}} : </label>
          <input class="form-control" v-model="attr[index]"/>
        </div>
        <div class="input-group mb-3" v-else >
          <label class="input-group-text" >Form {{keys}} : </label>
          <input class="form-control" type="number" min="1900" v-model="attr[index]"/>
          <label class="input-group-text" >To {{keys}} : </label>
          <input class="form-control" type="number" min="1900" max="2022" v-model="attr[index+3]"/>
        </div>
      </div>
      <button @click.prevent="submited()" class="btn btn-primary mb-3">Szukaj</button>
    </form>
  </div>
</template>

<script>
import movies from "../../public/movies.json"
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
