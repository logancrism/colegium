<script >
  import { defineComponent } from 'vue';
  import { Head, Link } from '@inertiajs/vue3';

  export default defineComponent({
    components: {
          Head,
      },

      props: {
        estudiante: {},
        asistencias: [],
      },

      data() {
          return {
            asistenciasEstudiante: {}
          }
      },

      watch: {
      },

      methods: {
        buscarAsistencias() {
          let buscarAsistencias = this.asistencias
          let q = buscarAsistencias.filter(obj => {
            console.log(obj)
            return obj.alumnos_id === this.estudiante.id
          })
          this.asistenciasEstudiante = q
        },

        bgAsistencia(tipo) {
          if (tipo == 'presente') {
            return 'bg-green-400'
          } else if (tipo == 'ausente') {
            return 'bg-red-400'
          } else {
            return 'bg-orange-400'
          }
        }
      },

      created () {

      },

      mounted() {
        this.buscarAsistencias()
      },

      computed: {
      },
  });
</script>

<template>
  <div class="shadow-lg bg-gray-100 text-center rounded p-4 w-auto">
    <img :src="estudiante.foto"  class="rounded-full border border-4 border-white shadow-lg avatar">
    <p class="mt-2">
      <span class="font-semibold text-xl ">{{ estudiante.nombre }} {{ estudiante.Apellido }}</span>
    </p>
    <div class="mt-2">
      <div class="inline-flex space-x-2">
        <div :class="bgAsistencia(asistencia.asistencia)" class="px-5 py-3 rounded-full text-2xl text-semibold text-white" v-for="asistencia in asistenciasEstudiante">
            <span v-if="asistencia.asistencia == 'presente'">P</span>
            <span v-else-if="asistencia.asistencia == 'ausente'">A</span>
            <span v-else>L</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
  .avatar { width: 200px; margin: 0 auto;  }
</style>
