<script lang="ts">
	import { onMount } from 'svelte';
	import '../app.css';

	onMount(() => {
		runGoogleAnalytics();
	});

	async function runGoogleAnalytics() {
		//  Google tag (gtag.js) - Google Analytics

		const hostname = location.hostname;

		if (hostname.startsWith('deploy-preview') || hostname.includes('--')) {
			console.log('Deployment preview on Netlify: skipped running Google Analytics.');
		} else if (hostname === 'localhost') {
			console.log('Local development: skipped running Google Analytics.');
		} else {
			const analyticsScript = await loadScript(
				'https://www.googletagmanager.com/gtag/js?id=G-54Q685VHKL'
			);

			// @ts-ignore
			window.dataLayer = window.dataLayer || [];
			function gtag() {
				// @ts-ignore
				dataLayer.push(arguments);
			}
			// @ts-ignore
			gtag('js', new Date());
			// @ts-ignore
			gtag('config', 'G-54Q685VHKL');
		}
	}

	function loadScript(src: string) {
		return new Promise((resolve, reject) => {
			const script = document.createElement('script');
			script.async = true;
			script.src = src;

			document.body.appendChild(script);

			script.addEventListener('load', () => resolve(script));
			script.addEventListener('error', () => reject(script));
		});
	}
</script>

<slot />
