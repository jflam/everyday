<!--
	Plan:

	1. DONE Create a simple day component within App.svelte
	2. DONE Add event handler for click to toggle complete state for that day
	3. DONE Refactor day component into day.svelte file and import into app.svelte
	4. DONE Write a loop to create a month's worth of day components
	5. DONE Write a loop to create a year's worth of day components
	6. Make CSS table responsive
	7. Add a Svelte store for persisting the state of those components
	8. Wire up the Svelte store to local browser storage
	9. Create some designs for the 365 calendar (perhaps modeled after the github activity tracker)
	10. Add routes that accomodate different goals (e.g., floss or cook meal)
	11. Add a way to synchronize user state to an OAuth based file store, e.g., Dropbox or OneDrive
	12. Add a way to synchronize user state to Fluid Framework and repackage app as a Fluid component
-->

<script>
import Day from './Day.svelte'

const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

function daysInMonth (month, year) { 
    return new Date(year, month, 0).getDate(); 
} 

const year = 2020;
const daysInJan = daysInMonth(1, year);
</script>

<main>
<div>
	{#each months as month, month_index}
	<div>
		{month}
		{#each Array(daysInMonth(month_index + 1, year)) as _, i}
			<Day />
		{/each}
	</div>
	{/each}
</div>
</main>

<style>
	div {
		display: table;
		width: 100%;
		table-layout: fixed;
	}

	div > div {
		display: table-cell;
		min-width: 50px;
		width: 50%;
	}
    main {
            max-width: 240px;
            margin: 0 auto;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>