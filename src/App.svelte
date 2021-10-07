<script>
	export let name;
	import Quiz from "./Quiz.svelte";
	import Declarations from "./Declarations.svelte";
	import Statements from "./Statements.svelte";
	import Each from "./Each.svelte";
	import Await from "./Await.svelte";
	import ComponentEvent from "./ComponentEvent/App.svelte";
	import ComponentBindings from "./ComponentBindings/App.svelte";
	import OnMount from "./OnMountLifeCycle.svelte";
	import Store from "./Store/App.svelte";
</script>

<main>
	<!--
	<h1>Hello {name}!</h1>

	<Quiz quizName="Another Quiz Name"/>
	<Declarations />

	<Statements />
	

	<Each />
	

	<Await />
	

	<ComponentEvent />

	<ComponentBindings />

-->
<OnMount />

<Store />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
