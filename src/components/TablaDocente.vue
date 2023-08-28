<template>
    <div class="container">
        <h1>Tabla de Docentes</h1>
        <table>
            <thead>

                <tr>
                    <th>Codigo</th>
                    <th>Cedula</th>
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Telefono</th>
                    <th>Email</th>
                    <th>Grado</th>
                    <th>Grupo</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="docente in docentes" :key="docente.codigo">
                <td>{{  docente.codigo}}</td>
                <td>{{ docente.cedula }}</td>
                <td>{{ docente.nombre }}</td>
                <td>{{ docente.apellido }}</td>
                <td>{{ docente.telefono }}</td>
                <td>{{ docente.email }}</td>
                <td>{{ docente.grado }}</td>
                <td>{{ docente.grupo }}</td>
                </tr>

                <router-view />

            </tbody>


        </table>
    </div>

</template>

<script>
import axios from "axios";

export default {
    data(){
        return{
            docentes: [],
        };
    },
    methods: {
        obtenerDocentes(){
            //Metodo para obtener la lista de docentes 
            axios.get("http://localhost:8080/api/docentes/listar")
            .then((response)=> {
                this.docentes = response.data;
            })
            .catch((error)=> {
                console.error("Error al obtener docentes: ", error);
            });
        },
    },
    mounted(){
        //Llamar al metodo para obtener la lista de estudiantes al cargar el componente
        this.obtenerDocentes();
    },
};
</script>