<template>

  <section class="src-componentes-resultados">
    <div class="jumbotron">
      <h2>Resultados</h2>
      <br>

      <div class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Numero de Pregunta</th>
            <th>Resultado</th>
          </tr>
          <tr>
            <td>1</td>
            <td>d</td>
          </tr>
          <tr>
            <td>2</td>
            <td>c</td>
          </tr>
          <tr>
            <td>3</td>
            <td>b</td>
          </tr>
        </table>
      </div>      

    </div>
  </section>

</template>


<script>

  export default  {
    name: 'src-componentes-resultados',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-componentes-resultados {

  }

  .jumbotron {
    background-color: green;
    color: white;
  }
</style>