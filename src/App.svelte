<!--
	Plan:

	1. DONE Create a simple day component within App.svelte
	2. DONE Add event handler for click to toggle complete state for that day
	3. DONE Refactor day component into day.svelte file and import into app.svelte
	4. DONE Write a loop to create a month's worth of day components
	5. DONE Write a loop to create a year's worth of day components
	6. DONE Make CSS table responsive
	7. DONE Make CSS table printable
	8. DONE Create CSS tooltips that show the dates
	9. Make CSS tooltips dynamic, i.e., on right side of screen they display whole tooltip vs. clipping
	10. DONE: Add a Svelte store for persisting the state of those components
	11. DONE: Wire up the Svelte store to local browser storage
	12. Create some designs for the 365 calendar (perhaps modeled after the github activity tracker)
	13. Add routes that accomodate different goals (e.g., floss or cook meal)
	14. Add a way to synchronize user state to an OAuth based file store, e.g., Dropbox or OneDrive
	15. Add a way to synchronize user state to Fluid Framework and repackage app as a Fluid component
-->

<script>
import Day from './Day.svelte'

const headings = ['Day', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

function daysInMonth (month, year) { 
    return new Date(year, month, 0).getDate(); 
} 

const year = 2020;
</script>

<div>
	{#each headings as heading, i}
		<div style="--column:{i + 1}; --row:{1}">{heading}</div>
	{/each}
	{#each Array(31) as _, i}
		<div style="--column:{1}; --row:{i + 2}">{i + 1}</div>
	{/each}
	{#each Array(12) as _, m}
		{#each Array(daysInMonth(m + 1, year)) as _, d}
			<Day column={m + 2} row={d + 2} date={new Date(year, m, d + 1)}/>
		{/each}
	{/each}
</div>

<style>
	div {
		display: grid;
	}
	div > div {
		grid-column: var(--column);
		grid-row: var(--row);
		margin: 5px;
	}
	@media print {
		@page {
			margin: 0 auto;
		}
		div { 
			transform-origin: top left;
			transform: scale(0.8);
		} 
	}
</style>