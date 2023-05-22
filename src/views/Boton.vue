<script setup>
import Swal from 'sweetalert2'
import router from "../router/router"
import { ref } from 'vue'
let hoverNext = ref(false)
let hoverBack = ref(false)
let intro = 'Ves un boton... Lo quieres oprimir cierto? Pero que hace esto? Es seguro? Que consecuencias trae? No tienes ni idea ¿cierto?, ahora imagina a tu abuela usando esto, se volvera loca! Pero que pasa si te paras encima?'
let conclusion = 'Muchas veces un boton pequeño no nos proporciona suficiente informacion, un simple signo debe ser capaz de expresar una idea, como un + o un -... Con este patron de diseño se idea permitir que aquellas personas novatas no teman de "romper algo"'
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
const showAnotherMessage = () =>{
    Swal.fire({
        title: 'Al hacer click...',
        text: 'Te va a mostrar otro mensaje de saludo',
        icon: 'info',
        showCancelButton: true,
        confirmButtonColor: 'rgb(61, 220, 133)',
        cancelButtonColor: 'rgba(22, 22, 50, 0.732)',
        cancelButtonText: 'Cancelar',
        confirmButtonText: 'Continuar'
    }).then((result) => {
        if (result.isConfirmed) {
            Swal.fire('Hola!!!', 'Has oprimido un boton 😎', 'success')
        }
    })
}
</script>
<template>
    <div class="container">
        <h2 class="title">Botones que si informan</h2>
        <p class="text">{{ intro }}</p>
        <section class="example">
            <button class="button" @click="showAnotherMessage()">Oprimeme!!!</button>
        </section>
        <p class="text">{{ conclusion }}</p>
        <section class="example">
            <button class="button next" @click="showMessage('Vas a ir a la seccion de bienvenida', '/')"><span class="material-symbols-outlined">arrow_back</span></button>
            <button class="button next" @click="showMessage('Vas a ir a la sección de barras de busqueda', '/barras-busqueda/')"><span class="material-symbols-outlined">arrow_forward</span></button>
        </section>
    </div>
</template>