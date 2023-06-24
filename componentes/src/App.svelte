<script>
	import Header from "./Desing/Header.svelte";
	import CardGrid from "./Posts/CardGrid.svelte";
	import InputCustom from "./Desing/InputCustom.svelte";

	const color = "danger"

	let titulo = ''
	let descripcion= ''
	let imagen = ''

	let posts = [
		{
			id: '1', 
			titulo: 'Trabajando con svelte', 
			descripcion:'Realizando el curso de svelte',
			imagen:'https://cdn.pixabay.com/photo/2023/05/11/13/11/man-7986401_1280.jpg'
		},
		{
			id: '2', 
			titulo: 'Trabajando con vie', 
			descripcion:'Realizando el curso de vie',
			imagen:'https://cdn.pixabay.com/photo/2023/05/07/09/59/mountains-7976041_1280.jpg'
		},
		{
			id: '3', 
			titulo: 'Trabajando con angular', 
			descripcion:'Realizando el curso de angular',
			imagen:'https://cdn.pixabay.com/photo/2023/05/09/07/18/space-7980556_1280.jpg'
		}
		]

		function agregarPost(){
			const nuevoPost = {
				id: Math.random().toString(),
				titulo: titulo,
				descripcion: descripcion,
				imagen: imagen
			}
			
			posts = [nuevoPost, ...posts]
		}
</script>

<Header {color} titulo="Componentes"/>

<div class="container">
	<CardGrid {posts}/>	

	<form on:submit|preventDefault={agregarPost}>
		<InputCustom 
			type="text" 
			nombre="Titulo" 
			id="titulo" 
			placeholder="Titulo" 
			value={titulo} 
			on:input={event => (titulo = event.target.value)}
		/>

		<InputCustom 
			type="text" 
			nombre="Imagen" 
			id="imagen" 
			placeholder="Imagen" 
			value={imagen} 
			on:input={event => (imagen = event.target.value)}
		/>

		<InputCustom 
			control="textarea"
			nombre="Descripcion" 
			id="descripcion" 
			placeholder="Descripcion" 
			value={descripcion} 
			on:input={event => (descripcion = event.target.value)}
		/>

		<button type="submit" class="btn btn-info">Guardar</button>

		<!--<input type="text" placeholder="Titulo" bind:value={titulo}>
		<input type="text" placeholder="Descripcion" bind:value={descripcion}>
		<input type="text" placeholder="Imagen" bind:value={imagen}>
		<button type="submit" class="btn btn-info">Guardar</button>-->
	</form>
</div>

