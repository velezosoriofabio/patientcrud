<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h1>Crear Nuevo Paciente</h1>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="agregarPaciente">
                    <!-- Documento -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Documento de identidad</span>
                        <input v-model="paciente.doc" required type="number" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <!-- Nombre -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Nombres</span>
                        <input v-model="paciente.name" required  type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
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
                            <option value="Compensar">Nueva EPS</option>
                            <option value="Compensar">SaludTotal</option>
                            <option value="Otra">Otra</option>
                        </select>
                    </div>
                    <!-- Pruebas del Perfil Lipídico -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol Total (mg/dL)</span>
                        <input v-model="paciente.cholt" required type="number" step="0.01" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol HDL (mg/dL)</span>
                        <input v-model="paciente.hdl" required type="number" step="0.01" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Colesterol LDL (mg/dL)</span>
                        <input v-model="paciente.ldl" required type="number" step="0.01" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                        <span class="input-group-text" id="inputGroup-sizing-default">Triglicéridos (mg/dL)</span>
                        <input v-model="paciente.trig" required type="number" step="0.01" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>

                    <!-- Botones -->
                    <div class="btn-group" role="group" aria-label="">
                        <button type="submit" class="btn btn-success">Guardar</button>
                        <router-link :to="{name:'listar'}" class="btn btn-danger">Cancelar</router-link>
                    </div>
                </form>
            </div>
            <div class="card-footer text-muted">
                Ingeniería de software 2024-2
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            paciente:{}
        }
    },
    methods:{
        agregarPaciente(){
            console.log(this.paciente)
            let datosPaciente={
                id:null,
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
            fetch('http://localhost/api/?insertar=1',{
                method: 'POST',
                body: JSON.stringify(datosPaciente),
                mode: 'no-cors'
            })
            .then(response => response.text())
            .then((data)=>{
                console.log(data)
                window.location.href='listar'
            })
        }
    }

}
</script>