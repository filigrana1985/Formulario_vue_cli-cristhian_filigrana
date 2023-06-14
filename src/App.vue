<template>
  <div class="container">
    <h2 class="h2 text-center text-danger">Formulario de Datos</h2>
    <form @submit.prevent="submitForm" ref="formulario" class="form-container">
      <div class="form-group">
        <label>Nombre:</label>
        <input type="text" class="form-control" v-model="nombre" required>
      </div>

      <div class="form-group">
        <label>Email:</label>
        <input type="email" class="form-control" v-model="email" required>
      </div>

      <div class="form-group">
        <label>Edad:</label>
        <input type="number" class="form-control" v-model="edad" min="0" required>
      </div>

      <div class="form-group">
        <label>Teléfono:</label>
        <input type="tel" class="form-control" v-model="telefono" pattern="[0-9]{10}" required>
      </div>

      <button type="submit" class="btn btn-success">Enviar</button>
    </form>

    <hr>

    <h2>Datos ingresados:</h2>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Email</th>
          <th>Edad</th>
          <th>Teléfono</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(persona, index) in personas" :key="index">
          <td>{{ persona.nombre }}</td>
          <td>{{ persona.email }}</td>
          <td>{{ persona.edad }}</td>
          <td>{{ persona.telefono }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.h2 {
  text-align: center;
  color: red;
}

.form-container {
  max-width: 400px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 10px;
}

label {
  display: block;
}

input[type="text"],
input[type="email"],
input[type="number"],
input[type="tel"] {
  width: 100%;
}
</style>

<script>
export default {
  data() {
    return {
      nombre: '',
      email: '',
      edad: '',
      telefono: '',
      personas: []
    };
  },
  methods: {
    submitForm() {
      if (this.$refs.formulario.checkValidity()) {
        this.personas.push({
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
