<script>
	import Modal from './Modal.svelte'
	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal
	}
	let people = [
		{name:'Akinwumi', beltColor:'red', age:'26', id:1 },
		{name:'Sammie', beltColor:'blue', age:'27', id:2 },
		{name:'Jide', beltColor:'green', age:'28', id:3 },
	]
	const handleClick = (id) =>{
		people = people.filter((person) => person.id != id );
	}


</script>

<Modal 
message="Hey, I am a prop value"
isPromo=(true) 
showModal={showModal} 
on:click={toggleModal}
/>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{#each people as person (person.id)}
	<div>
		<h4>{person.name}</h4>
		{#if person.beltColor == 'red'}
			<h1>Master Ninja</h1>
		{/if}
		<p>{person.age} years old, {person.beltColor} belt.</p>
		<button on:click={() => handleClick(person.id)}>delete</button>
	</div>
	{:else}
	<p>There are no people to show......</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>