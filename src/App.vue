<template>
  <div>
    <Formulario @form-submit="handleFormSubmit" />
    <Tabla :personas="personas" />
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue';
import Tabla from './components/Tabla.vue';

export default {
  components: {
    Formulario,
    Tabla
  },
  data() {
    return {
      personas: []
    };
  },
  methods: {
    handleFormSubmit(persona) {
      this.personas.push(persona);
    }
  }
};
</script>
