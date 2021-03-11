<script>
import HeroDetail from "./HeroDetail.svelte";
import HeroesList from "./HeroesList.svelte";

	export let name;
	
	const hero = {
		name: 'Batman',
		company: 'DC'
	}

	const heroes = [
		{id: 100, name: 'Kopek'},
		{id: 101, name: 'Kedi'},
		{id: 102, name: 'Aslan'},
	]
</script>

<main>
	<h1>Hello {name}!</h1>
	<!-- <HeroDetail {hero} /> -->
	<HeroesList />
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