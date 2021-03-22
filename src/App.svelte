<script>
	import Todos from './Todos.svelte'; 
</script>

<main>
	<h1>My To-Do List!</h1>
	<Todos />
</main>

<style>
	main {
		text-align: center;
		padding: 2em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #005cc8;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: 100%;
		}
	}
</style>