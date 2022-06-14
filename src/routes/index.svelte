<script context="module">
	export const prerender = true;
</script>

<script>
	import { onMount } from 'svelte';
	// import Counter from '$lib/Counter.svelte';
	const title = 'morpion'.toUpperCase();
	let tiles = [];
	let turn = 0;
	let player1 = '';
	let player2 = '';
	let computer = '';
	let chosen =""
	let chosenIcon = false;
	const symbols = [
		{
			id:0,
			name: 'cross',
			icon: 'fas fa-times'
		},
		{
id: 1,
			name: 'circle',
			icon: 'far fa-circle'
		}
	];
	// const { name, icon } = symbols;

	function launchGame() {
		tiles = ['', '', '', '', '', '', '', '', ''];
	}
	function chooseIcon(val) {
		console.log(val)
		chosen=val
		console.log(val)
		return chosen
	}
	onMount(() => launchGame());

	function fillTile(pos, sym) {
		turn++;

		console.log(pos, sym.name);
		sym = sym[turn % 2 === 0 ? 0 : 1].icon;

		tiles[pos] = sym;

		return tiles;
	}
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<section>
	<h1>
		{title}
	</h1>
	{#if !chosenIcon}
		<h2>Choisissez une icône</h2>
		<div class="cards">
			{#each symbols as { name, icon }}
			<label for="icon">
				<input name="icon" type="radio" id="icon" on:click={chooseIcon(name)} bind:value={icon} class="card">
					<i class="{icon} fa-fw fa-7x" />
			</label>
			{/each}
			<div>selected: {chosen}</div>
		</div>
	{:else}
		<div class="grid">
			{#each tiles as tile, i}
				<div on:click|once={() => fillTile(i, symbols)} class="tile">
					<span class="{tile} fa-4x" />
				</div>
				<!-- <div on:click={()=>fillTile(i, "ok")} class="tile">{tile}</div> -->
			{/each}
		</div>
		<div class="center">
			<button on:click={launchGame} class="">relancer</button>
		</div>
	{/if}
	<!-- <div class="playboard"> -->
	<!-- </div> -->

	<!-- <Counter /> -->
</section>

<style>
	.playboard {
		/* n-width: 300px; */
		margin: 0 auto;
		text-align: center;
	}
	.grid {
		margin: 50px auto;
		width: 332px;
		height: 332px;
		display: grid;
		grid-template-rows: repeat(3, auto);
		grid-template-columns: repeat(3, auto);
		box-sizing: border-box;
		place-items: center center;
		border-collapse: collapse;
		grid-gap: 1em;
		/* border-top: 2px solid #444;
		border-left: 2px solid #444; */
	}
	.cards {

		display: grid;
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 2em;
		/* justify-content: center; */
		/* place-items: center center; */
	}
	.card {
		position: absolute;
		display: flex;
		height: 150px;
		margin: 0 1em;
		width: 150px;
		border: 2px solid transparent;
		border-radius: 2em;
		transition: border 300ms linear;
		justify-content: center;
		/* place-self: center center; */
	}
	.card i {
		place-self: center;
	}
	.card:hover {
		border: 2px solid black;
	}

	.tile {
		display: flex;
		width: 100px;
		height: 100px;
		border-radius: 20%;
		background: white;
		align-items: center;
		justify-content: center;
		/* font-size: xx-large; */
		border: 1px solid hsla(0, 5%, 50%, 0.5);

		/* border-bottom: 2px solid #444;
		border-right: 2px solid #444; */
	}
	h1 {
		font-size: 2.5em;
		font-weight: 400;
		text-align: center;
	}

	@media screen and (min-width: 480px) {
	}
	i {
		position: relative;
		left: 22px;
		top: 20px;
	}
	/* 
	.tile div {
		place-self: center center; 
		align-self: center;
		justify-self: center;
		
	}
	*/

	/* section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	} */
</style>
