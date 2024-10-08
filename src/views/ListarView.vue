<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h1>Lista de Pacientes</h1>
            </div>
            <div class="card-body">
                <table class="table">
                    <thead>
                        <tr>
                            <th>No.</th>
                            <th>Documento</th>
                            <th>Nombre y Apellidos</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="paciente in pacientes" v-bind:key="paciente.id">
                            <td scope="row">{{ paciente.id}}</td>
                            <td>{{ paciente.doc}}</td>
                            <td>{{ paciente.name}} {{paciente.lastname }}</td>
                            <td>
                                <div class="btn-group" role="group" aria-label="">
                                    <button type="button" class="btn btn-success">Resultados</button>
                                    <button type="button" class="btn btn-primary">Editar</button>
                                    <button type="button" class="btn btn-danger">Borrar</button>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
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
            pacientes:[]
        }
    },
    created:function (){
        this.consultarPacientes();
    },
    methods:{
        consultarPacientes(){
            fetch('http://localhost/api/')
            .then(response => response.json())
            .then((data)=>{
                console.log(data)
                this.pacientes = [];
                if(typeof data[0].success === 'undefined'){
                    this.pacientes = data
                }
            })
            .catch(console.log)
        }
    }
}
</script>