<template>
  <WyszukiwanieFilmow @submit="submited" />
  <TableaZfilmami :attr = "this.sub"/>
  <div>
  </div>
</template>

<script>
import TableaZfilmami from './components/TableaZfilmami.vue';
import WyszukiwanieFilmow from './components/WyszukiwanieFilmow.vue'

export default {
  data(){
    return{
      sub : [],
    }
  },
  components: {
    WyszukiwanieFilmow,
    TableaZfilmami
  },
  methods: {
    submited(n) {
      this.sub = n 
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
