<script>
	import netlifyIdentity from 'netlify-identity-widget';
	import { onMount } from 'svelte';

	// Following these instructions: https://decapcms.org/docs/add-to-your-site/

	onMount(() => {
		netlifyIdentity.init();

		netlifyIdentity.on('init', (user) => {
			if (!user) {
				netlifyIdentity.on('login', () => {
					document.location.href = '/admin/';
				});
			}
		});
	});
</script>

<h1 class="text-3xl font-bold underline">Hello Tailwind!</h1>
<h2>Welcome to SvelteKit</h2>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
