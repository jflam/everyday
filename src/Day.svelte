<script>
    export let clicked = false;

	function handleClick() {
		clicked = !clicked;
	}
</script>

<div on:click={handleClick} class={clicked ? 'selected': ''}></div>

<style>
	div {
        border: solid black;
	 	height: 20px; 
		width: 20px;
		background-color: white;
        margin: 5px;
	}

	.selected {
		background-color: green;
	}
</style>