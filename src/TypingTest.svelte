<script>
	let test = "The Wolf in Sheep's Clothing Once upon a time.";
	let testArray = test.split("");

	// users input
	let input = "";
	$: userInputArray = input.split("");

	let start = false;

	/**
	 * Equations
	 * https://www.speedtypingonline.com/typing-equations
	 */
	let timer = 60;
	$: wpm = (userInputArray.length/5)/1;


	// set reactivity here

	setInterval(() => {

		if(start) {
			if (timer > 0) timer--;
		}

		
	}, 1000);

	let accuracy = 0;


	$: input && revealScore();

	const revealScore = () => {

		let score = [];

		testArray.map((e,i) => {
			if(e == userInputArray[i]) {
				score.push(e)
			}

			console.log(e)
		})

		accuracy = (score.length / testArray.length) * 100;

		console.log("score is: ", score)
	}

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

<div>Timer: {timer}</div>
<div>Accuracy: {accuracy.toFixed(2)}</div>
<div>WPM: {wpm.toFixed(2)}</div>

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
