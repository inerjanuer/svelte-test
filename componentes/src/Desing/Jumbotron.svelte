<script>
    import { onMount, onDestroy, beforeUpdate, afterUpdate, tick } from "svelte";
    export let nombre

    let mostrar

    function entrar(){
        mostrar = true
    }

    function salir() {
        mostrar = false
    }

    // creacion
    // scripts
    console.log("Se ejecuta primero")
    // onMount
    onMount(async () => {
        console.log("se ejecuta tercer lugar")
        await tick()
        console.log("Se ejecuta cuando todos los metodos ya se ejecutaron")
    })
    // onDestroy
    onDestroy(() => {
        console.log("Se ejecuta cuando se elimina el componente")
    })


    // actualizacion del dom
    // beforeupdate

    beforeUpdate(() => {
        console.log("se ejecuta antes de actualizar el dom")
    })
    // afterUpdate

    afterUpdate(() => {
        console.log("Se ejecuta despues de actualizar el dom")
    })
    // tick


</script>

<style>
    h2 {
        color: red;
        font-weight: bolder;
        text-decoration: underline;
    }

    p {
        text-align: justify;
        color: blue;
        text-transform: uppercase;
        font-style: italic;
    }
</style>

<div class="jumbotron mt-4" on:mouseenter={entrar} on:mouseleave={salir}>
    <h1>{nombre}</h1>
    <h2>
        <slot name="subtitulo">
            <span>Agregar subtitulo aqui.</span>
        </slot>
    </h2>
    <p>
        <slot name="parrafo">
            <span>Agregar parrafo aqui.</span>
        </slot>
    </p>
    <slot mostrar={mostrar}></slot>
</div>