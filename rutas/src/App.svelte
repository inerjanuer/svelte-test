<script>
import Router from 'svelte-spa-router'
import { link, push } from 'svelte-spa-router'
import routes from './routes.js'

let nombre = 'Svelte'

function pagina() {
	push('/Acerca/123')
}
</script>

<nav class="navbar navbar-expand-lg bg-body-tertiary">
	<div class="container-fluid">
	  <span class="navbar-brand" href="#">Svelte rutas</span>
	  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
		<span class="navbar-toggler-icon"></span>
	  </button>
	  <div class="collapse navbar-collapse" id="navbarSupportedContent">
		<ul class="navbar-nav me-auto mb-2 mb-lg-0">
		  <li class="nav-item">
			<a class="nav-link" href="/" use:link>Inicio</a>
		  </li>
		  <li class="nav-item">
			<a class="nav-link" href="/Acerca/123/{nombre}" use:link >Acerca de</a>
		  </li>
		  <li class="nav-item">
			<a class="nav-link" href="/Contactos" use:link>Contactos</a>
		  </li>
		</ul>
	  </div>
	</div>
  </nav>

  <button class="btn btn-warning" on:click={pagina}>Acerca</button>
  <Router {routes} />