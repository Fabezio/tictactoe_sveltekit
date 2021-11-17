<script context="module">
	export const prerender = true;
</script>

<script>
	import Counter from '$lib/Counter.svelte';
	const title = "morpion".toUpperCase()
	let symbols = [
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
	function fillTile(pos, sym) {
		console.log(pos, sym)
		symbols[pos]=sym
		return symbols

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
			{#each symbols as symbol,i}
			<div on:click={()=>fillTile(i, "ok")} class="cell">{symbol}</div>
			{/each}
			<!-- <div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div>
			<div class="cell">token</div> -->
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
	.cell {
		display: flex;
		width: 100px;
		height: 100px;
		border-radius: 20%;
		background: white;
		align-items: center;
		justify-content: center;
		font-size: xx-large;
		border: 1px solid hsla(0, 5%, 50%, .5);

		/* border-bottom: 2px solid #444;
		border-right: 2px solid #444; */
		
	}
	/* 
	.cell div {
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
