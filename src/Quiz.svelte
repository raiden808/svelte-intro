<script>
    
    // adding export enables props modification
    // for modification, use let instead of const
    export let quizName = "Test Quiz Name";

    let title = "";

    //calcs
    let a = 0;
    let b = 0;


    let result = "";
    let correntAnswer = "a";

    function pickAnswer(answer) {
        if(answer === correntAnswer) {
            return (result = "Correct")
        }

        result = "OOPS";
    }
</script>


<div>
    <h2>{quizName}</h2>
    <h2>{title}</h2>
    <input bind:value={title} type="text" />


    <!--Simple Calculator-->
    <h2>Calculator</h2>
    <input bind:value={a} type="number" />
    <input bind:value={b} type="number" />
    <h2>{a+b}</h2>

    {#if result}
        <h4>{result}</h4>
    {:else}
        <h4>Please pick an answer</h4>
    {/if}


    <!--Events-->
    <div>
        <button on:click={() => {pickAnswer('a')}}>A</button>
        <button on:click={() => {pickAnswer('b')}}>B</button>
        <button on:click={() => {pickAnswer('c')}}>C</button>
        <button on:click={() => {pickAnswer('d')}}>D</button>
    </div>
</div>