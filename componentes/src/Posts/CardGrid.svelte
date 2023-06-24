<script>
    import Card from "./Card.svelte";
    export let posts
    let evento = 'aqui no hay nada'

    function verMas(e){
        alert('Ver mas info')
        console.log(e.detail.id)
        evento = e.detail.id
    }

    function favorito(e) {
        alert('Favoritos')
        evento = e.detail
    }
</script>

<div class="row mt-3">
    {#each posts as post }
    <div class="col-sm-4">
		<Card titulo={post.titulo} imagen={post.imagen} descripcion={post.descripcion} 
        on:ver-mas={verMas}
        on:favorito={favorito}/>	
    </div>
	{/each}
</div>
<h1>{evento}</h1>