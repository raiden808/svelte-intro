<script>
	let test = "The Wolf in Sheep's Clothing Once upon a time, a Wolf decided to disguise the way he looked. He thought it would help him get food more easily. He put on the skin of a sheep, then he went out with the flock into the pasture. Even the shepherd was fooled by his clever costume. In the evening, the shepherd put him in with the rest of the sheep. He closed the gate and made sure it was secure before he went to bed. In the middle of the night, he came back to the fold to get some meat for the next day. Instead of a sheep, though, he grabbed the Wolf, killing him instantly. Those who look to harm others will be harmed themselves.";
	let testArray = test.split("");

	// users input
	let input = "";
	$: userInputArray = input.split("");

	let start = false;

	const startTest = () => {
		start = !start;

		// const
		console.log(testArray)
	};

	let key;
	let keyCode;
	function handleKeydown(event) {
		key = event.key;
		keyCode = event.keyCode;

		let removeKeys = ["Shift", "Backspace","Control"];

		// if(start) {
			if(!removeKeys.includes(key)){
				input+=key
				console.log('input is: ', input)
			}		
		// }
	}
</script>

<div>
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
</div>

<br />
<br />
<textarea bind:value={input} />


<button on:click={startTest}>{start}</button>
<h2>Hello</h2>


<!-- <svelte:window on:keydown={handleKeydown}/> -->

<style>

	textarea {
		width: 100%;
		height: 150px;
		padding: 12px 20px;
		box-sizing: border-box;
		border: 2px solid #ccc;
		border-radius: 4px;
		background-color: #f8f8f8;
		font-size: 16px;
		resize: none;
	}
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
