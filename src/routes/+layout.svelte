<script>
	import '../app.css';

	function initializeCms() {
		//@ts-ignore
		if (window?.netlifyIdentity) {
			//@ts-ignore
			window.netlifyIdentity.on('init', (user) => {
				if (!user) {
					//@ts-ignore
					window.netlifyIdentity.on('login', () => {
						document.location.href = '/admin/';
					});
				}
			});
		}
	}
</script>

<svelte:head>
	<script
		src="https://identity.netlify.com/v1/netlify-identity-widget.js"
		on:load={initializeCms}
	></script>
</svelte:head>

<slot />
