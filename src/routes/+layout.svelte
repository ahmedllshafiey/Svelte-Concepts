<script>
	import favicon from '$lib/assets/favicon.svg';
	import '../global.css';
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Svelte Concepts</title>
</svelte:head>

{@render children()}
