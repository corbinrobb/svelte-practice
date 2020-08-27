<script>
	import Facts from './components/Facts.svelte';
	let count = 0;
	const handleClick = () => {if (count < 10) count += 1}
</script>

<main>
	<h1>Simple Pointless App</h1>
	<p>{count}</p>
	<button on:click={handleClick}>Increase</button>
	{#if count >= 10}
		<p>WOOOOOO!!!</p>
	{:else if count > 5}
		<p>Gotta Want It!</p>
	{:else}
		<p>Click ten times for cat facts!</p>
	{/if}
	{#if count >= 10}
		<Facts/>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		font-size: 3rem;
		text-transform: uppercase;
		font-weight: 300;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>