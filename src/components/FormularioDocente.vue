<template>
    <div class="container">
        <h1>Formulario registro Docentes</h1>
        <form id="Docenteform" @submit.prevent="guardar">
            <div class="formgroup">
                <label for="codigo">Codigo </label>
                <input type="text" id="codigo" name="codigo" required v-model="codigo">
            </div>
            <div class="formgroup">
                <label for="cedula">Cedula </label>
                <input type="text" id="cedula" name="cedula" required v-model="cedula">
            </div>
            <div class="formgroup">
                <label for="nombre">Nombre </label>
                <input type="text" id="nombre" name="nombre" required v-model="nombre"> 
            </div>
            <div class="formgroup">
                <label for="apellido">Apellido </label>
                <input type="text" id="apellido" name="apellido" required v-model="apellido"> 
            </div>
            <div class="formgroup">
                <label for="telefono">Telefono </label>
                <input type="text" id="telefono" name="telefono" required v-model="telefono"> 
            </div>
            <div class="formgroup">
                <label for="email">Email </label>
                <input type="text" id="email" name="email" required v-model="email"> 
            </div>
            <div class="formgroup">
                <label for="grado">Grado </label>
                <input type="text" id="grado" name="grado" required v-model="grado"> 
            </div>
            <div class="formgroup">
                <label for="grupo">Grupo </label>
                <input type="text" id="grupo" name="grupo" required v-model="grupo"> 
            </div>

            <button type="submit" id="guardar" name="guardar">Guardar</button><br />
            <button type="button" id="eliminar" name="eliminar" @click="eliminar">Eliminar</button><br />
            <button type="button" id="actualizar" name="actualizar" @click="actualizar">Actualizar</button><br />
            <button type="button" id="consultar" name="consultar" @click="consultar">Consultar</button><br />

        </form>

    </div>


</template>

<script>
import axios from "axios";

export default {

    data() {
        return {
            codigo: "",
            cedula: "",
            nombre: "",
            apellido: "",
            telefono: "",
            email: "",
            grado: "",
            grupo: "",
        };
    },

    methods: {
        guardar(){

            axios
                .post("http://localhost:8080/api/docentes", {
                    codigo: this.codigo,
                    cedula: this.cedula,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    telefono: this.telefono,
                    email: this.email,
                    grado: this.grado,
                    grupo: this.grupo,
                })
                .then((response)=> {
                    console.log("Docente registrado de manera exitosa:",response.data);
                    alert("Exito");
                    this.codigo = '';
                    this.cedula = '';
                    this.nombre = '';
                    this.apellido = '';
                    this.telefono = '';
                    this.email = '';
                    this.grado = '';
                    this.grupo = '';
                 
                })
                .catch((error) => {
                    console.error("Error no se ha podido realizar el registro del docente:",error);
                });
        },

        consultar(){

            axios
                .get('http://localhost:8080/api/docentes/'+this.codigo)
                .then((response)=>{
                    //Actualizar los campos del formulario con los datos del docente que se quiere consultar
                    this.cedula = response.data.cedula;
                    this.nombre = response.data.nombre;
                    this.apellido = response.data.apellido;
                    this.telefono = response.data.telefono;
                    this.email = response.data.email;
                    this.grado = response.data.grado;
                    this.grupo = response.data.grupo;
                })
                .catch((error) => {
                    console.error("Error al consultar al doccente",error);
                });
        },

        actualizar (){

            axios
                .put("http://localhost:8080/api/docentes/actualizar/"+this.codigo, {
                    codigo: this.codigo,
                    cedula: this.cedula,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    telefono: this.telefono,
                    grado: this.grado,
                    grupo: this.grupo,
                })
                .then((response)=>{
                    console.log("El Docente ha sido actualizado exitosamente",response.data);
                })
                .catch((error) => {
                    console.error("Error al actualizar docente:",error);
                });
        },
 
        eliminar(){

            axios
                .delete("http://localhost:8080/api/docentes/"+this.codigo)
                .then(()=>{
                    console.log("Docente elimanado exitosamente");
                    //Limpiar los campos del formulario despues de realizar la eliminacion
                    this.codigo="";
                    this.cedula="";
                    this.nombre="";
                    this.apellido="";
                    this.telefono="";
                    this.email="";
                    this.grado="";
                    this.grupo="";
                })
                .catch((error) => {
                    console.error("error al eliminar docente:",error);
                });
        },

    },
};
</script>