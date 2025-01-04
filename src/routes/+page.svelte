<script>
	import { onMount, onDestroy } from 'svelte';
	import { io } from 'socket.io-client';

	let socket;

	onMount(() => {
		socket = io('http://localhost:5001');

		socket.on('connect', () => {
			console.log('Connected:', socket.id);
		});

		socket.on('welcome', (message) => {
			console.log('Server says:', message);
		});

		socket.emit('my_event', 'Hello from Svelte client!');

		socket.on('my_response', (data) => {
			console.log('Response from server:', data);
		});
	});

	onDestroy(() => {
		if (socket) {
			socket.disconnect();
		}
	});
</script>

<main>
	<h1>Svelte + Go Socket.IO Exp</h1>
</main>
