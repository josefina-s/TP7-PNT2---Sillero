<template>

  <section class="src-componentes-tabla">
    <div class="jumbotron">
      <h2>Usuarios</h2>
      <br>
      <button class="btn btn-success my-3 mr-3" @click="getUsuarios()">GET</button>
      <button class="btn btn-danger my-3 mr-3" @click="usuarios = []">Clear</button>
      <br>

      <div v-if="this.usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>

          </tr>
          <tr v-for="(usuario,index) in usuarios" :key="index">
                   <td>{{ usuario.nombre }}</td>
                  <td>{{ usuario.edad }}</td>
                  <td>{{ usuario.email }}</td>
                
              </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-warning text-center">No hay usuarios disponibles</h4>

    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-tabla',
    props: [],
    mounted () {

    },
    data () {
      return {
        usuarios: [],
        url: 'https://633f79d2e44b83bc73bae575.mockapi.io/posts',
      }
    },
    methods: {
      getUsuarios() {
        this.axios(this.url)
          .then( respuesta => { this.usuarios = respuesta.data })
          .catch( error => console.error(error))
      }
    },
    computed: {

    }
}

</script>

<style scoped lang="css">
  .jumbotron {
    background-color: #bdf8cf;
    font-family: 'Fira Sans', sans-serif;
  }
</style>
