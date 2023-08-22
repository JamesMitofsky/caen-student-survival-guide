<!-- Following this: https://joyofcode.xyz/sveltekit-google-analytics -->

<script lang="ts">
	import { page } from '$app/stores';

	$: {
		// the page isn't a preview on Netlify
		if (typeof gtag !== 'undefined') {
			console.log('gtag exists: sending pageview');
			gtag('config', 'G-54Q685VHKL', {
				page_title: document.title,
				page_path: $page.url.pathname
			});
		}
	}
</script>

<svelte:head>
	<script async src="https://www.googletagmanager.com/gtag/js?id=G-54Q685VHKL">
	</script>
	<script>
		// verify location for analytics
		const hostname = location.hostname;

		if (hostname === 'localhost') {
			console.log('-- Localhost: no analytics');
		} else if (hostname.includes('--')) {
			console.log('-- Netlify preview: no analytics');
		} else {
			console.log('-- Not localhost or Netlify preview: adding gtag script');
			window.dataLayer = window.dataLayer || [];

			function gtag() {
				dataLayer.push(arguments);
			}

			gtag('js', new Date());
			gtag('config', 'G-54Q685VHKL');
		}
	</script>
</svelte:head>
