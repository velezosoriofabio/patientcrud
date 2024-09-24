<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h1>Página para CREAR los pacientes</h1>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="agregarPaciente">
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Documento</span>
                        <input v-model="paciente.doc" required type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Nombre</span>
                        <input v-model="paciente.name" required  type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="inputGroup-sizing-default">Apellidos</span>
                        <input v-model="paciente.lastname" required type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                    </div>

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
            paciente: {}
        }
    },
    methods:{
        agregarPaciente(){
            console.log(this.paciente)
            let datosPaciente={
                id:null,
                doc:this.paciente.doc,
                name:this.paciente.name,
                lastname:this.paciente.lastname
            }
            fetch('http://localhost/api/?insertar=1',{
                method: 'POST',
                body:JSON.stringify(datosPaciente)
            })
            .then(response=>response.json())
            .then((data)=>{
                console.log(data)
                window.location.href='listar'
                })
        }
    }
    
}
</script>