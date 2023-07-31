<script>
    export let params = {}
</script>

<h1>Pagina acerca</h1>
<h1>Id recibido: {params.id}</h1>
{#if params.nombre}
<h1>Nombre recibido: {params.nombre}</h1>
{/if}