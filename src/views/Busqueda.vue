<script setup>
import router from '../router/router'
import Swal from 'sweetalert2'
import { ref } from 'vue'
let nombre = ref('')
const validarNumeros = (evento) =>{
    let condicion = false
    if(evento.keyCode >= 48 && evento.keyCode <= 57 || evento.keyCode == 8){
        return evento
    }else{
        evento.preventDefault()
    }
}
const showMessage = (texto, pathTo) =>{
    Swal.fire({
        title: 'Al hacer click...',
        text: texto,
        icon: 'info',
        showCancelButton: true,
        confirmButtonColor: 'rgb(61, 220, 133)',
        cancelButtonColor: 'rgba(22, 22, 50, 0.732)',
        cancelButtonText: 'Cancelar',
        confirmButtonText: 'Continuar'
    }).then((result) => {
        if (result.isConfirmed) {
            router.push({path: pathTo})
        }
    })
}
const showAnotherMessage = (texto) =>{
    Swal.fire({
        title: 'Este es un campo de texto',
        text: texto,
        icon: 'info',
        showCancelButton: false,
        confirmButtonColor: 'rgb(61, 220, 133)',
        confirmButtonText: 'Continuar'
    })
}
</script>
<template>
    <div class="container">
        <h1 class="title">Las barras de busqueda</h1>
        <p class="text">Las barras de busqueda son utiles para mandar informacion a una pagina web. Pero te has preguntado ¿Que informacion? ¿Como escribirla? Ese problema es de software de la prehistoria, con este patron de diseño sabras que elementos llevan comas, puntos, mayusculas o minusculas.</p>
        <section class="example">
            <input type="text" class="input" placeholder="Ingresa tu nombre" v-model="nombre" @click="showAnotherMessage('Debes estar seguro que tu nombre esta bien escrito')">
        </section>
        <h2 class="text">{{ nombre }}</h2>
        <section class="example">
            <input type="text" class="input" placeholder="Ingresa tu telefono" @keydown="evento => validarNumeros(evento)" @click="showAnotherMessage('Debes ingresar numeros unicamente, no es aceptado ningun caracter especial ni letra')">
        </section>
        <p class="text">Esto es util no solo para el usuario por si este presenta dudas durante el uso, tambien es util para evitar problemas a la hora de subir formularios ya que especifica que informacion debe ir en cada campo y que restricciones tiene. Facilitando el almacenamiento de informacion en las bases de datos.</p>
        <section class="example">
            <button class="next button" @click="showMessage('Vas a ir a la seccion de botones', '/boton/')"><span class="material-symbols-outlined">arrow_back</span></button>
            <button class="next button" @click="showMessage('Vas a ir a la sección de links', '/links/')"><span class="material-symbols-outlined">arrow_forward</span></button>
        </section>
    </div>
</template>