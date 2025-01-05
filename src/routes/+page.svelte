<script>
	import io from 'socket.io-client';
	import { onMount } from 'svelte';
	const socket = io('http://localhost:8080');

	onMount(() => {
		socket.emit('my_event', 'Hello from Svelte');
		socket.on('my_response', (data) => {
			console.log('Response from server:', data);
		});
	});
</script>

<main>
	<h1>Svelte + Go Socket.IO Exp</h1>
</main>

<style>
	h1 {
		color: yellow;
	}
</style>
