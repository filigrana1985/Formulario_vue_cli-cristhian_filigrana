<template>
  <div class="form-group mx-auto">
    <h2 class="text-center">Formulario de Datos</h2>
    <form @submit.prevent="submitForm" ref="formulario">
      <div class="row">
        <div class="form-group col-md-6 text-center">
          <label for="nombre">Nombre:</label>
          <input type="text" v-model="nombre" required class="form-control" id="nombre">
        </div>

        <div class="form-group col-md-6 text-center">
          <label for="email">Email:</label>
          <input type="email" v-model="email" required class="form-control" id="email">
        </div>
      </div>

      <div class="row">
        <div class="form-group col-md-6 text-center">
          <label for="edad">Edad:</label>
          <input type="number" v-model="edad" min="0" required class="form-control" id="edad">
        </div>

        <div class="form-group col-md-6 text-center">
          <label for="telefono">Teléfono:</label>
          <input type="tel" v-model="telefono" pattern="[0-9]{10}" required class="form-control" id="telefono">
        </div>
      </div>

      <div class="text-center mt-3">
        <button type="submit" class="btn btn-primary">Enviar</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'FormularioVue',
  data() {
    return {
      nombre: '',
      email: '',
      edad: '',
      telefono: ''
    };
  },
  methods: {
    submitForm() {
      if (this.$refs.formulario.checkValidity()) {
        this.$emit('form-submit', {
          nombre: this.nombre,
          email: this.email,
          edad: this.edad,
          telefono: this.telefono
        });
        this.resetForm();
      }
    },
    resetForm() {
      this.nombre = '';
      this.email = '';
      this.edad = '';
      this.telefono = '';
    }
  }
};
</script>
  
  <style>
  .form-input {
    margin-bottom: 10px;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .form-button {
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .form-button:hover {
    background-color: #45a049;
  }
  </style>
  