<template>

  <section class="src-componentes-navbar">
    <nav class="navbar navbar-expand-md navbar-dark bg-dark">
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/notas">
              <a class="nav-link" href="#">Notas</a>
            </router-link>
          </li>
          <li class="nav-item">
            <router-link to="/respuestas">
              <a class="nav-link" href="#">Respuestas</a>
            </router-link>
          </li>
        </ul>
      </div>
    </nav>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-navbar',
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
  .src-componentes-navbar {

  }
</style>
