<template>

  <section class="src-components-notas">
    <div class="jumbotron">
      <h2><i><b>Ingreso de notas</b></i></h2>

      <vue-form :state="formState" @submit.prevent="enviar()">
    
        <validate tag="div">
          <label for="nombre">Nombre</label>
          <input 
            type="text"
            id="nombre"
            name="nombre" 
            class="form-control"
            autocomplete="off"
            v-model.trim="formData.nombre" 
            required 
            :minlength="nombreMinLength"
            :maxlength="nombreMaxLength"
            no-espacios
          />

          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo requiere como mínimo {{nombreMinLength}} caracteres.
            </div>
            <div slot="no-espacios" class="alert alert-danger mt-1">
              No se permiten espacios intermedios en este campo.
            </div>
            <div slot="maxLength" class="alert alert-danger mt-1">
              El nombre debe tener como maximo {{nombreMaxLength}} caracteres.
            </div>
          </field-messages>
        </validate>
        <br>

        <validate tag="div">
          <label for="apellido">Apellido</label>
          <input 
            type="text"
            id="apellido"
            name="apellido" 
            class="form-control"
            autocomplete="off"
            v-model.trim="formData.apellido" 
            required 
            :minlength="nombreMinLength"
            :maxlength="nombreMaxLength"
            no-espacios
          />

          <field-messages name="apellido" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo requiere como mínimo {{nombreMinLength}} caracteres.
            </div>
            <div slot="no-espacios" class="alert alert-danger mt-1">
              No se permiten espacios intermedios en este campo.
            </div>
            <div slot="maxLength" class="alert alert-danger mt-1">
              El nombre debe tener como maximo {{nombreMaxLength}} caracteres.
            </div>
          </field-messages>
        </validate>
        <br>

        <validate tag="div">
          <label for="nota">Nota</label>
          <input 
            type="number"
            id="nota"
            name="nota" 
            class="form-control"
            autocomplete="off"
            v-model.number="formData.nota" 
            required 
            :min="notaMin"
            :max="notaMax"
          />

          <field-messages name="nota" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="min" class="alert alert-danger mt-1">
              La nota mínima permitida es {{notaMin}}.
            </div>
            <div slot="max" class="alert alert-danger mt-1">
              La nota máxima permitida es {{notaMax}}.
            </div>
          </field-messages>
        </validate>
        <br>

        <button class="btn btn-success my-4" :disabled="formState.$invalid">Enviar</button>
      </vue-form>
      <br>

      <div v-if="notas.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre de alumno</th>
            <th>Nota</th>
          </tr>
          <tr v-for="(nota,index) in notas" :key="index">
            <td>{{ nota.nombreCompleto }}</td>
            <td :style="{color: analizarNota(nota.nota).color }">{{ nota.nota }}</td>
          </tr>
          <tr>
            <td :style="{color: analizarNota(obtenerPromedio()).color }">PROMEDIO NOTAS: {{obtenerPromedio()}}</td>
          </tr>
        </table>
      </div>
      <h3 v-else class="alert alert-info">No hay notas ingresados</h3>

    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-notas',
    props: [],
    mounted () {

    },
    data () {
      return {
        formState : {},
        formData : this.getInicialData(),
        nombreMinLength : 3,
        nombreMaxLength: 15,
        notaMin: 0,
        notaMax: 10,
        notas: []
      }
    },
    methods: {
      getInicialData() {
        return {
          nombre: '',
          apellido: '',
          nota: '',
        }
      },

      enviar() {
        let nota = {...this.formData}       
        nota.nombreCompleto = `${nota.nombre} ${nota.apellido}`

        this.notas.push(nota)

        this.formData = this.getInicialData()
        this.formState._reset()
      },

      analizarNota(nota){
        let color = 'green'
        if( nota>= 0 && nota<4) color = 'red'
        if( nota>= 4 && nota<7) color = 'yellow'
        return {
          color
        }
      },

      obtenerPromedio(){
        let sumatoria = 0
        this.notas.forEach(nota => {
          sumatoria += nota.nota
        });
        return sumatoria/this.notas.length     
        }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-notas {

  }
  .jumbotron {
    background-color: #6691ed;
  }
</style>
