<script>
	export let clicked = false;

	function handleClick() {
		clicked = !clicked;
	}
</script>

<div on:click={handleClick} class={clicked ? 'selected': ''}></div>

<style>
	div {
		/* TODO: parameterize height once refactored into component */
	 	height: 50px; 
		width: 50px;
		background-color: black;
        margin: 5px;
	}

	.selected {
		background-color: blue;
	}
</style>