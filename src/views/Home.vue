<script setup>
import router from "../router/router"
import Swal from 'sweetalert2'
import { ref } from 'vue'
let tamaño = window.innerWidth
let hover = ref(false)
const showMessage = () =>{
    Swal.fire({
        title: 'Al hacer click...',
        text: 'Vas a dirigirte a la sección de Botones...',
        icon: 'info',
        showCancelButton: true,
        confirmButtonColor: 'rgb(61, 220, 133)',
        cancelButtonColor: 'rgba(22, 22, 50, 0.732)',
        cancelButtonText: 'Cancelar',
        confirmButtonText: 'Continuar'
    }).then((result) => {
        if (result.isConfirmed) {
            router.push({path: '/boton/'})
        }
    })
}
</script>
<template>
    <div class="container">
        <h1 class="title">¡Bienvenido!</h1>
        <p class="text">Nuestra visión es la de un mundo que no tenga limites, y para empezar a hacer realidad este mundo necesitamos que todas las personas, sin importar quien, puedan ingresar a cualquier lado sin miedo a romper algo, el aprendizaje es cuestión de divertirse en el trayecto, jugando y palpando todo aquello que se encuentra a su alrededor, y eso es lo que buscamos hacer...</p>
        <section class="example">
            <button class="button next" @click="showMessage()"><span class="material-symbols-outlined">arrow_forward</span></button>
        </section>
    </div>
</template>