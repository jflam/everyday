<script>
    import { writable } from 'svelte/store';
    import { onMount, afterUpdate } from 'svelte';

    export let clicked = writable(false);
    export let column = 1;
    export let row = 1;
    export let date = Date.now();

    let isInitializing = true;
    const dateFormat = { weekday: 'short', year: 'numeric', month: 'short', day: 'numeric' };

	function handleClick() {
        $clicked = !$clicked;
    }

    onMount(async() => {
        const key = Number(date).toString(36);
        const raw = JSON.parse(localStorage.getItem(key));
        const val = raw !== null ? raw : false;

        if (val === true) {
            $clicked = val;
        }
    });

    afterUpdate(() => {
        if (isInitializing) {
            isInitializing = false;
        } else {
            const key = Number(date).toString(36);
            if ($clicked === true) {
                localStorage.setItem(key, $clicked.toString());
            } else {
                localStorage.removeItem(key);
            }
        }
    });
</script>

<div style="--column:{column};--row:{row}" on:click={handleClick} class={$clicked === true ? 'selected': ''}>
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