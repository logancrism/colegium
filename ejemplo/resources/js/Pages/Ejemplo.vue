<script >
  import { defineComponent } from 'vue';
  import { Head, Link } from '@inertiajs/vue3';
  import Card from "@/Components/Card.vue"


  export default defineComponent({
    components: {
          Head,
          Card
      },

      props: {
      },

      data() {
          return {
            alumnos: [],
            asistencias: []
          }
      },

      watch: {
      },

      methods: {

        getAlumnos() {
          window.axios('https://x8ki-letl-twmt.n7.xano.io/api:Yg52T3Tp/alumnos')
          .then( (req)=> {
            this.alumnos = req.data
          } )
        },

        getAsistencias() {
          window.axios('https://x8ki-letl-twmt.n7.xano.io/api:Yg52T3Tp/asistencias')
          .then( (req) => {
            this.asistencias = req.data
          })
        }

      },

      created () {
        this.getAlumnos()
        this.getAsistencias()
      },

      mounted() {
      },

      computed: {
      },
  });
</script>

<template>
  <div class="w-full max-w-4xl mx-auto bg-gray-200 shadow-lg rounded-lg border border-gray-200 relative text-center text-semibold mt-4">
    <h1 class="text-2xl">Prueba Tecnica Colegium - Cristihan Andres Monroy</h1>
      <div class=" mt-5 w-full p-4 grid gap-4 grid-cols-3" >
        <div class="w-full " v-for="alumno in alumnos" >
          <Card :asistencias="asistencias"  :estudiante="alumno"></Card>
        </div>
      </div>
</div>
</template>

