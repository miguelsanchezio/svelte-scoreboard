<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [
		{
			name: 'Edgar Kanter',
			points: 51
		},
		{
			name: 'Gerald Mayor',
			points: 35,
		},
		{
			name: 'Annie Solo',
			points: 67
		}
	];

	const addPlayer = e => {
		const newPlayer = e.detail;
		players = [...players, newPlayer]
		console.log(newPlayer);
	}

	const removePlayer = e => {
		const playerName = e.detail;
		players = players.filter(player => player.name !== playerName);
	}
</script>

<Navbar/>
<AddPlayer on:addplayer={addPlayer}/>
<div class="container">
	{#if players.length === 0}
		<p>No Players Found...</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
		{/each}
	{/if}
</div>


<style>

</style>
