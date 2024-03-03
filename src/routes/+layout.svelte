<script>
	import Header from '$lib/Header.svelte';
	import Footer from '$lib/Footer.svelte';
	import '../app.pcss';
</script>

<div class="flex flex-col h-screen">
    <div class="sticky top-0 z-50">
		<Header />
	</div>

    <div class="grow bg-gradient-to-r from-cyan-500 to-blue-500">
		<slot />
	</div>

    <div class="sticky bottom-0 z-50">
		<Footer />
	</div>
</div>