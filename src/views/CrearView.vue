/* eslint-disable */
<template>
  <div class="container mt-5">
    <div class="text-end mb-3">
      <img src="../assets/logo.png" alt="Logo" class="img-fluid" style="max-width: 150px;">
    </div>
    <div class="card">
      <div class="card-header text-center text-white">
        <h4 class="form-title">Formulario de Registro de Paciente</h4>
      </div>
      <div class="card-body">
        <form @submit.prevent="agregarPaciente">
          <!-- Documento de identidad -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="documento" class="col-form-label">Documento de identidad:</label>
            <div class="col-auto">
              <input type="number" class="form-control text-center" id="documento" v-model="paciente.doc" placeholder="Ingrese el documento" style="width: 300px;">
            </div>
          </div>
          <!-- Nombre -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="nombre" class="col-form-label">Nombre:</label>
            <div class="col-auto">
              <input type="text" class="form-control text-center" id="nombre" v-model="paciente.name" placeholder="Ingrese el nombre" style="width: 300px;">
            </div>
          </div>
          <!-- Apellido -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="apellido" class="col-form-label">Apellido:</label>
            <div class="col-auto">
              <input type="text" class="form-control text-center" id="apellido" v-model="paciente.lastname" placeholder="Ingrese el apellido" style="width: 300px;">
            </div>
          </div>
          <!-- Edad -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="edad" class="col-form-label">Edad:</label>
            <div class="col-auto">
              <input type="number" class="form-control text-center" id="edad" v-model="paciente.edad" placeholder="Ingrese la edad" style="width: 300px;">
            </div>
          </div>
          <!-- Género -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="genero" class="col-form-label">Seleccionar género:</label>
            <div class="col-auto">
              <select class="form-select" id="genero" v-model="paciente.genero" style="width: 300px;">
                <option selected>Seleccionar género</option>
                <option value="Masculino">Masculino</option>
                <option value="Femenino">Femenino</option>
                <option value="Otro">Otro</option>
              </select>
            </div>
          </div>
          <!-- EPS -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="eps" class="col-form-label">Seleccionar EPS:</label>
            <div class="col-auto">
              <select class="form-select" id="eps" v-model="paciente.eps" style="width: 300px;">
                <option selected>Seleccionar EPS</option>
                <option value="Sanitas">Sanitas</option>
                <option value="Nueva EPS">Nueva EPS</option>
                <option value="Coosalud">Sura</option>
                <option value="Comfama">SaludTotal</option>
                <option value="SaludCoop">Compensar</option>
              </select>
            </div>
          </div>
          <!-- Colesterol total -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="cholesterol" class="col-form-label">Colesterol total - CHOLT (mg/dL)</label>
            <div class="col-auto">
              <input type="number" step="0.01" class="form-control text-center" id="cholesterol" v-model="paciente.cholt" placeholder="Ingrese el colesterol total" style="width: 300px;">
            </div>
          </div>
          <!-- HDL -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="hdl" class="col-form-label">Lipoproteínas de Alta Densidad – HDL (mg/dL)</label>
            <div class="col-auto">
              <input type="number" step="0.01" class="form-control text-center" id="hdl" v-model="paciente.hdl" placeholder="Ingrese HDL" style="width: 300px;">
            </div>
          </div>
          <!-- LDL -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="ldl" class="col-form-label">Lipoproteínas de Baja Densidad – LDL (mg/dL)</label>
            <div class="col-auto">
              <input type="number" step="0.01" class="form-control text-center" id="ldl" v-model="paciente.ldl" placeholder="Ingrese LDL" style="width: 300px;">
            </div>
          </div>
          <!-- Triglicéridos -->
          <div class="row mb-3 justify-content-center align-items-center">
            <label for="trig" class="col-form-label">Triglicéridos - TRIG (mg/dL)</label>
            <div class="col-auto">
              <input type="number" step="0.01" class="form-control text-center" id="trig" v-model="paciente.trig" placeholder="Ingrese triglicéridos" style="width: 300px;">
            </div>
          </div>
          <!-- Botones -->
          <div class="text-center mt-4">
            <button type="submit" class="btn btn-primary btn-lg">Guardar</button>
            <router-link :to="{ name: 'listar' }" class="btn btn-secondary btn-lg ms-2">Cancelar</router-link>
          </div>
        </form>
      </div>
      <div class="card-footer text-muted text-center">
        @Ingeniería de Software 2024-2
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      paciente: {}
    };
  },
  methods: {
    agregarPaciente() {
      console.log(this.paciente);
      let datosPaciente = {
        id: null,
        doc: this.paciente.doc,
        name: this.paciente.name,
        lastname: this.paciente.lastname,
        edad: this.paciente.edad,
        genero: this.paciente.genero,
        eps: this.paciente.eps,
        cholt: this.paciente.cholt,
        hdl: this.paciente.hdl,
        ldl: this.paciente.ldl,
        trig: this.paciente.trig
      }
      fetch('http://localhost/api/?insertar=1', {
        method: 'POST',
        body: JSON.stringify(datosPaciente),
        mode: 'no-cors'
      })
      .then(response => response.text())
      .then((data) => {
        console.log(data);
        window.location.href = 'listar';
      })
      .catch((error) => {
        console.error('Error:', error);
      });
    }
  }
};
</script>

<style scoped>
/* Modificar el color del título específicamente */
.card-header {
  background-color: #2D3E50 !important; /* Cambia el color del header */
}

/* Centrar la imagen */
.img-fluid {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

/* Estilo para las etiquetas */
label {
  background-color: #2D3E50;
  color: white;
  text-align: center;
  width: 150px; /* Ancho reducido para las etiquetas */
}

/* Estilo para el tamaño y la alineación de los inputs y selects */
.form-control, .form-select {
  width: 300px; /* Mantiene el ancho de los campos */
  text-align: center; /* Centra el texto dentro de los campos */
}

/* Estilo para centrar las filas */
.row {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Estilo para el botón de guardar */
.btn-primary {
  background-color: #007bff; /* Color del botón de guardar */
  border-color: #007bff; /* Color del borde del botón */
}

/* Estilo para el botón de cancelar */
.btn-secondary {
  background-color: #6c757d; /* Color del botón de cancelar */
  border-color: #6c757d; /* Color del borde del botón */
}

/* Estilo para el título del formulario */
.form-title {
  width: 300px;
  margin: auto;
}
</style>