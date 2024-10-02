<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h1>Página para CREAR los pacientes</h1>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="agregarPaciente">
                    <!-- Código Consecutivo -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Código Consecutivo</span>
                        <input v-model="paciente.codigo" required type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Documento -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Documento</span>
                        <input v-model="paciente.doc" required type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Nombre -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Nombre</span>
                        <input v-model="paciente.name" required  type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Apellidos -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Apellidos</span>
                        <input v-model="paciente.lastname" required type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Edad -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Edad</span>
                        <input v-model="paciente.edad" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Género (Lista desplegable) -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Género</span>
                        <select v-model="paciente.genero" required class="form-select" aria-label="Default select example">
                            <option value="" disabled selected>Seleccionar Género</option>
                            <option value="Masculino">Masculino</option>
                            <option value="Femenino">Femenino</option>
                            <option value="Otro de los 92 generos">Otro</option>
                        </select>
                    </div>
                    <!-- EPS (Lista desplegable) -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">EPS</span>
                        <select v-model="paciente.eps" required class="form-select" aria-label="Default select example">
                            <option value="" disabled selected>Seleccionar EPS</option>
                            <option value="Sura">Sura</option>
                            <option value="Sanitas">Sanitas</option>
                            <option value="Compensar">Compensar</option>
                            <option value="Otra">Otra</option>
                        </select>
                    </div>
                    <!-- Pruebas del Perfil Lipídico -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol Total (mg/dL)</span>
                        <input v-model="paciente.colesterolTotal" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol HDL (mg/dL)</span>
                        <input v-model="paciente.colesterolHDL" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol LDL (mg/dL)</span>
                        <input v-model="paciente.colesterolLDL" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Triglicéridos (mg/dL)</span>
                        <input v-model="paciente.trigliceridos" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>

                    <!-- Botones -->
                    <div class="btn-group" role="group" aria-label="">
                        <button type="submit" class="btn btn-success">Guardar</button>
                        <router-link :to="{name:'listar'}" class="btn btn-danger">Cancelar</router-link>
                    </div>
                </form>
            </div>
            <div class="card-footer text-muted">
                @Ingeniería de Software 2024-2
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            paciente: {
                codigo: '',
                doc: '',
                name: '',
                lastname: '',
                edad: '',
                genero: '',
                eps: '',
                colesterolTotal: '',
                colesterolHDL: '',
                colesterolLDL: '',
                trigliceridos: ''
            }
        }
    },
    methods:{
        agregarPaciente(){
            console.log(this.paciente)
            let datosPaciente = {
                id: null,
                codigo: this.paciente.codigo,
                doc: this.paciente.doc,
                name: this.paciente.name,
                lastname: this.paciente.lastname,
                edad: this.paciente.edad,
                genero: this.paciente.genero,
                eps: this.paciente.eps,
                colesterolTotal: this.paciente.colesterolTotal,
                colesterolHDL: this.paciente.colesterolHDL,
                colesterolLDL: this.paciente.colesterolLDL,
                trigliceridos: this.paciente.trigliceridos
            }
            fetch('http://localhost/api/?insertar=1', {
                method: 'POST',
                body: JSON.stringify(datosPaciente)
            })
            .then(response => response.json())
            .then((data) => {
                console.log(data)
                window.location.href = 'listar'
            })
        }
    }
}
</script>