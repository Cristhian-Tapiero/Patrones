<script setup>
import router from '../router/router';
import Swal from 'sweetalert2';
import { ref } from 'vue'
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
const showMessageLink = (texto) =>{
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
            window.open('https://pbs.twimg.com/profile_images/815316964818067456/Pgo5JmX0_400x400.jpg', '_blank')
        }
    })
}
</script>
<template>
    <div class="container">
        <h1 class="title">Los links...</h1>
        <section class="example">
            <p class="text">Los links resultan ser desafiantes, muchas veces no sabemos a donde nos dirigen, que hacen, que contienen y aun si tienes conocimientos mas avanzados no sabes si son seguros 😲. <br/> Por esta razón, nuestro patron de diseño busca <a class="link" tabindex="1" @click="$swal('Hiciste click sobre un link', 'No todos los links redirigen a un lugar 😲', 'info')"> especificar  cada detalle</a> del link donde quieras hacer click</p>
        </section>
        <section class="example">
            <a tabindex="2" @click="showMessageLink('Te va a redirigir a una imagen con contenido sensible, no apto para todo el publico')" class="link">¡Has click sobre mi!</a>
        </section>
        <section class="example">
            <button class="button next" @click="showMessage('Vas a dirigirte a la sección de barras de busqueda', '/barras-busqueda/')"><span class="material-symbols-outlined">arrow_back</span></button>
            <button class="button next" @click="showMessage('Vas a dirigirte a la sección de bienvenida', '/')"> <span class="material-symbols-outlined">home</span></button>
        </section>
    </div>
</template>