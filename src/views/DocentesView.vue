<template>
    <div class="docente">
        <div class="components">
            <FormularioDocente/>
            <TablaDocente/>
        </div>
    </div>
</template>

<script>
import FormularioDocente from '@/components/FormularioDocente.vue';
import TablaDocente from '@/components/TablaDocente.vue';

export  default {
name: 'DocentesView',

    components: {
        FormularioDocente,
        TablaDocente
    }
}
</script>

<style>
body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to bottom,white,pink);
    min-height: 100vh;
    margin: 0;
    padding: 0;
}

.components{
    display: grid;
    grid-template-columns: 1fr 2fr;
    grid-auto-rows: 1fr;
}

.container {

    margin: 1rem;
    padding: 1rem;
    background-color: rgb(242, 202, 202);
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    border-radius: 5px;
}

h1 {

    text-align: center;
    margin-bottom: 20px;
}

.formgroup {

    margin-bottom: 15px;
}

form {
    padding: 2%;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input {
    width: 80%;
    padding: 3px;
    border: 1px solid rgb(195, 166, 166);
    border-radius: 3px;
}

button {

    display: block;
    width: 35%;
    margin: 0 auto;
    padding: 0.5 rem 1 rem;
    background-color: rgb(242, 76, 104);
    color: rgb(26, 27, 28);
    border: 10px;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
}

button:hover {
    background-color: rgb(250, 146, 164);
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
}

th, td {
    padding: 10px;
    text-align: center;
    border-style: solid;
}

tr {

    border-style: solid;
}

th {
    background-color: rgb(250, 146, 164);
    border-style: solid;
}

tr:hover {
    background-color: rgb(242, 76, 104);
}

</style>