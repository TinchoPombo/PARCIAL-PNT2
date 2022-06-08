<template>

  <section class="src-components-respuestas">
    <div class="jumbotron">
      <h2><i><b>Respuestas</b></i></h2>
      <br>
      <br>

      <table class="table table-dark">
        <tr>
          <th>Pregunta</th>
          <th>Respuesta</th>
        </tr>
        <tr v-for="(pregunta,index) in preguntas" :key="index">
          <td>{{ pregunta.pregunta }}</td>
          <td>{{ pregunta.respuesta }}</td>
        </tr>
      </table>
    </div>    
  </section>

</template>

<script>

  export default  {
    name: 'src-components-respuestas',
    props: [],
    mounted () {

    },
    data () {
      return {
        preguntas: [
          {
            pregunta:'1',
            respuesta:'C'
          },

          {
            pregunta:'2',
            respuesta:'C'
          },
          
          {
            pregunta:'3',
            respuesta:'B'
          }
        ]
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-respuestas {

  }
  .jumbotron{
    /* Permalink - use to edit and share this gradient: https://colorzilla.com/gradient-editor/#00b7ea+11,00b7ea+38,009ec3+100 */
background: rgb(0,183,234); /* Old browsers */
background: -moz-linear-gradient(top,  rgba(0,183,234,1) 11%, rgba(0,183,234,1) 38%, rgba(0,158,195,1) 100%); /* FF3.6-15 */
background: -webkit-linear-gradient(top,  rgba(0,183,234,1) 11%,rgba(0,183,234,1) 38%,rgba(0,158,195,1) 100%); /* Chrome10-25,Safari5.1-6 */
background: linear-gradient(to bottom,  rgba(0,183,234,1) 11%,rgba(0,183,234,1) 38%,rgba(0,158,195,1) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00b7ea', endColorstr='#009ec3',GradientType=0 ); /* IE6-9 */

  }
</style>
