<template>
  
  <div class="container">
    <h1 class="text-center mb-3">Listado de Canciones</h1>
    <div class="row mt-5">
      <div class="col-4">
        <form @submit.prevent="submit">
          <div class="mb-3">
            <p>Nombre Artista: 
            <input class="form-control" type="text" v-model="artista"/></p>
            <p>Canción:
            <input class="form-control" type="text" v-model="cancion"/> </p>
          </div>
          <button class="btn btn-success">Buscar Canción</button>
        </form>
      </div>
      <div class="col-8">
        
      </div>
    </div>
  </div>

</template>

<script>
import { consumirCanciones } from "./api";
import { Error404 }  from "./components/Error404.vue";


export default {
  name: 'App',
  components: { },
  data() {
    return {
      artista: "",
      cancion: "",
      letra: "",
      error: "",

    };

  },



  methods: {
    async submit() {
      console.log(`Se ejecuta el metodo submit`)
      

      // ejemplo 1
      //consumirCanciones(this.artista, this.cancion).then( letra => console.log(letra));
      // ejemplo 2
      const letraCancion = await consumirCanciones(this.artista, this.cancion);
      console.log(letraCancion)
    },
    //  created() {        this.letraCancion;      },
    mostrarInformacion() {
      return `Canción: ${this.cancion} de ${this.artista}`;
    }
  }
};


</script>

<style scoped>
body {
  background-color: black;
  color: white;
}


</style>
