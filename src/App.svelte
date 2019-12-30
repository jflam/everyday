<!--
	Plan:

	1. Create a simple day component within App.svelte
	2. Add event handler for click to toggle complete state for that day
	3. Refactor day component into day.svelte file and import into app.svelte
	4. Write a loop to create a week's worth of day components
	5. Add a Svelte store for persisting the state of those components
	6. Wire up the Svelte store to local browser storage
	7. Create some designs for the 365 calendar (perhaps modeled after the github activity tracker)
	8. Add routes that accomodate different goals (e.g., floss or cook meal)
	9. Add a way to synchronize user state to an OAuth based file store, e.g., Dropbox or OneDrive
	10. Add a way to synchronize user state to Fluid Framework and repackage app as a Fluid component
	
-->


<script>
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
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