<script>
    async function getRandomNumber() {
        const res = await fetch(
            `http://www.randomnumberapi.com/api/v1.0/random`,
            {
                mode: "cors", // 'cors' by default
            }
        )

       //  console.log(res.text().then(text => text.split(/\r|\n/)));

        const text = await res.text();

        console.log(text)

        if (res.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }

    let promise = getRandomNumber();

    function handleClick() {
        promise = getRandomNumber();
    }
</script>

<button on:click={handleClick}> generate random number </button>

{#await promise}
    <p>...waiting</p>
{:then number}
    <p>The number is {number}</p>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}
