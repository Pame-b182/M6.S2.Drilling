<template>
  <div id="app">
    <Tareas/>
  </div>
</template>

<script>
//Si el componente importado esta en muchas carpetas, conviene anteponer "@" para direccionarlo correctamente
import Tareas from '@/components/Tareas.vue'

export default {
  name: 'App',
  components: {
    Tareas
  }
}
</script>

<style>

</style>
