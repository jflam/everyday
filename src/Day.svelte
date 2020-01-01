<script>
    export let clicked = false;
    export let column = 1;
    export let row = 1;
    export let date = Date.now();

    const dateFormat = { weekday: 'short', year: 'numeric', month: 'short', day: 'numeric' };

	function handleClick() {
		clicked = !clicked;
	}
</script>

<div style="--column:{column};--row:{row}" on:click={handleClick} class={clicked ? 'selected': ''}>
    <span class="tooltip">{date.toLocaleDateString("en-US", dateFormat)}</span>
</div>

<style>
	div {
        border: solid black;
        border-width: thin;
	 	height: 1.5em; 
		width: 1.5em;
		background-color: white;
        margin: 5px;
        grid-column: var(--column);
        grid-row: var(--row);
	}
    div:hover .tooltip {
        visibility: visible;
    }
	.selected {
		background-color: green;
	}
    div .tooltip {
        visibility: hidden;
        position: relative;
        top: -20px;
        left: 25px;
        background: black;
        color: white;
        padding: 0px 5px 5px 5px;
        white-space: nowrap;
    }
</style>