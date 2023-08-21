<script>
	import '../app.css';
</script>

<svelte:head>
	{#if location.hostname.startsWith('deploy-preview') || location.hostname.includes('--')}
		<script>
			console.log(
				'Deployment preview on Netlify or hostname contains "--": skipped running Google Analytics.'
			);
		</script>
	{:else if location.hostname === 'localhost'}
		<script>
			console.log('Local development: skipped running Google Analytics.');
		</script>
	{:else}
		<script async src="https://www.googletagmanager.com/gtag/js?id=G-54Q685VHKL"></script>

		<script>
			window.dataLayer = window.dataLayer || [];
			function gtag() {
				dataLayer.push(arguments);
			}
			gtag('js', new Date());

			gtag('config', 'G-54Q685VHKL');
		</script>
	{/if}
</svelte:head>

<slot />
