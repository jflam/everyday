<script>
    export let clicked = false;
    export let column = 1;
    export let row = 1;

	function handleClick() {
		clicked = !clicked;
	}
</script>

<div style="--column:{column};--row:{row}" on:click={handleClick} class={clicked ? 'selected': ''}></div>

<style>
	div {
        border: solid black;
	 	height: 1.5em; 
		width: 1.5em;
		background-color: white;
        margin: 5px;
        grid-column: var(--column);
        grid-row: var(--row);
	}

	.selected {
		background-color: green;
	}
</style>