<script>
	import ContactCard from './ContactCard.svelte';

	let name = 'Ayesha';
	let title = '';
	let image = '';
	let description = '';
	let age = 24;

	// Reactive Variables
	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === 'Jownally') {
		console.log('it runs!');
		age = 25
	}
	///////////////////////////////////////

	function incrementAge() {
		age = age + 1;
	}

	function changeName() {
		name = 'Jownally'
	}

	function nameInput(event) {
		const enteredValue = event.target.value;
		name = enteredValue;
	}
</script>

<main>
	<h1>Hello {uppercaseName}, my age is {age}!</h1>
	<button on:click="{incrementAge}">Change Age</button>
	<!-- <button on:click="{changeName}">Change Name</button> -->

	<!--Binding to Element Properties-->
	<!-- <input type="text" value="{name}" on:input="{nameInput}"> -->
	<!----------------------------------------------------------->

	<!--Two Way Binding- change value of age when name is Jownally or only change name value-->
	<input type="text" bind:value="{name}">
	<input type="text" bind:value="{title}">
	<!---Deeper into Bindings-->
	<input type="text" bind:value="{image}">
	<textarea rows="3" bind:value="{description}"></textarea>
	
	<!--Props components-->
	<ContactCard username="{name}" jobTitle="{title}" description="{description}" userImage="{image}"/>
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
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>