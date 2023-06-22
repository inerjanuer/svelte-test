<script>
	let nombre = "Jorge";
	const name = "Sandra";
	nombre = "<strong style='color: red;''>Pedro</strong>" // no es recomendable utilizarlo

	let nombre2 = 'Jorge' 

	let v1 = 0
	let v2 = 0

	let check = false

	function alert1(){
		alert('alerta1');
	}

	const alert2 = () => alert('alerta 2') 

	let contador = 0
	let texto = ''
		$: resultado = contador * 10
	$: if (resultado % 3 === 0){
		texto = 'OK'
	} else {
		texto = 'Oooouch'
	}

	let login = true
	const cambio = () => login = !login

	let nombres = ['Maria', "Sandra", "Ruben"]

	let personas = [{"id": 1,
					"first_name": "Ephraim",
					"last_name": "Zohrer",
					"email": "ezohrer0@purevolume.com"
					}, {
					"id": 2,
					"first_name": "Carri",
					"last_name": "Sprague",
					"email": "csprague1@wired.com"
					}, {
					"id": 3,
					"first_name": "Patti",
					"last_name": "Keggins",
					"email": "pkeggins2@1688.com"
					}, {
					"id": 4,
					"first_name": "Lynn",
					"last_name": "Ziem",
					"email": "lziem3@bluehost.com"
					}, {
					"id": 5,
					"first_name": "Morganica",
					"last_name": "Bolderson",
					"email": "mbolderson4@desdev.cn"
					}, {
					"id": 6,
					"first_name": "Demetria",
					"last_name": "Lamerton",
					"email": "dlamerton5@over-blog.com"
					}, {
					"id": 7,
					"first_name": "Dorian",
					"last_name": "McQuaker",
					"email": "dmcquaker6@com.com"
					}, {
					"id": 8,
					"first_name": "Donny",
					"last_name": "Kendrick",
					"email": "dkendrick7@4shared.com"
					}, {
					"id": 9,
					"first_name": "Way",
					"last_name": "Jouhandeau",
					"email": "wjouhandeau8@prnewswire.com"
					}, {
					"id": 10,
					"first_name": "Sherm",
					"last_name": "Clue",
					"email": "sclue9@plala.or.jp"
					}]

	function sleep(s){
		return new Promise(res => setTimeout(res, s))
	}

	let promesa = ajax()
	let users = []
	const url = 'https://jsonplaceholder.typicode.com/users'

	async function ajax(){
		const res = await fetch(url)
		users = await res.json()
		await sleep(3000)
		if(res.ok){
			return users
		} else {
			throw new Error('Error al conectar con la api')
		}
	}
</script>

<main>
	<p>{@html nombre} {name}</p>

	<hr>
	<h1>Databinding</h1>
	<h2>{nombre2}</h2>
	<input type="text" bind:value={nombre2}>
	<hr>
	Valor 1 <input type="range" bind:value={v1}>
	Valor 2 <input type="range" bind:value={v2}> 
	<p>{v1} + {v2} = {v1 + v2}</p>
	<hr>
	Habilitar Boton
	<input type="checkbox" bind:checked={check}>
	<button disabled={!check}>Guardar</button>

	<h1>OnClick</h1>
	<button on:click={alert1}>Alerta 1</button>
	<button on:click={alert2}>Alerta 2</button>
	<button on:click={() => alert('alerta 3')}>Alerta 3</button>
	<hr>

	<h1>Variables Reactivas</h1>
	<button on:click={() => contador++}>Contador</button>
	<p>Contador: {contador}, Resultado x 10 {resultado}</p>
	<p>{texto}</p>

	<hr>
	<h1>Bloque If</h1>
	{#if login}
		<h2>Estas logueado</h2>
	{:else}
		<h2>Iniciar sesion</h2>
	{/if}
	<button on:click={cambio}>Login</button>

	<hr>
	<h1>Bloque each</h1>
	<ul>
		{#each nombres as nombre1, i }
			<li>{i + 1} {nombre1}</li>
		{/each}
	</ul>

	<hr>
	<table align="center">
		<th>Nombre</th>
		<th>Apellido</th>
		<th>Email</th>
		{#each personas as item}
			<tr>
				<td>{item.first_name}</td>
				<td>{item.last_name}</td>
				<td>{item.email}</td>
			</tr>
		{:else}			
			<tr>
				<td colspan="3"> La api no tiene datos</td>
			</tr>
		{/each}
	</table>

	<hr>
	<h1>Bloque Await</h1>
	{#await promesa}
		<p>Cargando Api...</p>	
	{:then usuarios} 
		{#each usuarios as item }
			<li>{item.name}</li>
		{/each}
	{:catch error}
		<p style="color: red;">{error}</p>
	{/await}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>