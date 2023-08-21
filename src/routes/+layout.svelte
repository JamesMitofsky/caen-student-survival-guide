<script>
	import '../app.css';

	function runGoogleAnalytics() {
		//  Google tag (gtag.js) - Google Analytics

		const hostname = location.hostname;

		if (hostname.startsWith('deploy-preview') || hostname.includes('--')) {
			console.log('Deployment preview on Netlify: skipped running Google Analytics.');
		} else if (hostname === 'localhost') {
			console.log('Local development: skipped running Google Analytics.');
		} else {
			const script = document.createElement('script');
			script.async = true;
			script.src = 'https://www.googletagmanager.com/gtag/js?id=G-54Q685VHKL';
			script.onload = () => {
				// @ts-ignore
				window.dataLayer = window.dataLayer || [];
				function gtag() {
					// @ts-ignore
					dataLayer.push(arguments);
				}
				gtag('js', new Date());
				gtag('config', 'G-54Q685VHKL');
			};
			document.head.appendChild(script);
		}
	}
</script>

<svelte:head>
	<script
		async
		src="https://www.googletagmanager.com/gtag/js?id=G-54Q685VHKL"
		on:load={runGoogleAnalytics}
	></script>
</svelte:head>

<slot />
