<script>
	let test = "The quick born fox jump over the lazy dog.";
	let testArray = test.split("");

	// users input
	let input = "";
	$: userInputArray = input.split("");

	const reveal = () => {
		console.log(test);

		// const

		// console.log(testArray)
	};
</script>

{#each testArray as item, i}
	{#if userInputArray.length > i}
		{#if testArray[i] != userInputArray[i]}
			<span class="wrong">{item}</span>
		{:else}
			<span class="right">{item}</span>
		{/if}
	{:else}
		<span class="normal">{item}</span>
	{/if}
{/each}

<textarea bind:value={input} />

<button on:click={reveal}>Test</button>
<h2>Hello</h2>

<style>
	.normal {
		color: black;
		text-decoration: underline;
	}

	.wrong {
		color: pink;
	}

	.right {
		color: green;
	}
</style>
