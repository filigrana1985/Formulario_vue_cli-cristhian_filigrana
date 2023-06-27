<template>
    <div>
      <h2>Datos ingresados:</h2>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">Nombre</th>
            <th scope="col">Email</th>
            <th scope="col">Edad</th>
            <th scope="col">Teléfono</th>
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
  
  <script>
  export default {
    name:'TablaVue',
    props: {
      personas: {
        type: Array,
        default: () => []
      }
    }
  };
  </script>
  