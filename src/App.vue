<template>
  <div class="container">
    <WyszukiwanieFilmow @submit="submited" />
    <TableaZfilmami :attr = "this.sub"/>
    <div class="row">
      <div class="col">
        <FilmyWgGatunku />
      </div>
      <div class="col">
        <FilmyWgObsady />
      </div>
    </div>
  </div>
  <hr>
</template>

<script>
import FilmyWgGatunku from './components/FilmyWgGatunku.vue';
import TableaZfilmami from './components/TableaZfilmami.vue';
import WyszukiwanieFilmow from './components/WyszukiwanieFilmow.vue'
import FilmyWgObsady from './components/FilmyWgObsady.vue';
import "bootstrap/dist/css/bootstrap.min.css"
export default {
  data(){
    return{
      sub : [],
    }
  },
  components: {
    WyszukiwanieFilmow,
    TableaZfilmami,
    FilmyWgGatunku,
    FilmyWgObsady
},
  methods: {
    submited(n) {
      this.sub = n 
    }
  }
  
}
</script>

<style>

</style>
