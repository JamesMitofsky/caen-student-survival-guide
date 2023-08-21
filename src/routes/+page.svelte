<script>
	// Following these instructions: https://decapcms.org/docs/add-to-your-site/
	function runNetlifyIdentity() {
		// @ts-ignore
		if (window.netlifyIdentity) {
			// @ts-ignore
			window.netlifyIdentity.on('init', (user) => {
				if (!user) {
					// @ts-ignore
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
		on:load={runNetlifyIdentity}
	></script>
</svelte:head>

<h1 class="text-3xl font-bold underline">Hello Tailwind!</h1>
<h2>Welcome to SvelteKit</h2>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
