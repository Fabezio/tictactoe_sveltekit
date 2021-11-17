<script context="module">
	export const prerender = true;
</script>

<script>
	import Counter from '$lib/Counter.svelte';
	const title = "morpion".toUpperCase()
	let tiles = [
		"",
		"",
		"",
		"",
		"",
		"",
		"",
		"",
		"",
	]
	let turn = 0
	const symbols={
		cross: "fas fa-times", 
		circle: "far fa-circle",
	}

		
	function fillTile(pos, sym) {
		turn++

		console.log(pos, sym)
		const {cross, circle} = symbols
		sym=(turn%2 === 0 ? cross : circle)

		tiles[pos]=sym

		
		return tiles

	}

	
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<section>
	<h1>
		{title}
	</h1>
	<!-- <div class="playboard"> -->
		<div class="grid">
			{#each tiles as tile,i}
			<div on:click={()=>fillTile(i, symbols.circle)} class="tile"><span class="{tile} fa-4x"></span></div>
			<!-- <div on:click={()=>fillTile(i, "ok")} class="tile">{tile}</div> -->
			{/each}
			
		</div>
	<!-- </div> -->


	<!-- <Counter /> -->
</section>

<style>
	.playboard{
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
	.tile {
		display: flex;
		width: 100px;
		height: 100px;
		border-radius: 20%;
		background: white;
		align-items: center;
		justify-content: center;
		/* font-size: xx-large; */
		border: 1px solid hsla(0, 5%, 50%, .5);

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
