<script>
	import { page } from '$app/stores';
</script>

<div class="error mt-8">
	<h1 class="font-semibold text-2xl">{$page.status}: {$page.error?.message}</h1>
	<p>If you want to report this error, please use the <a href="/contact">Contact form</a>.</p>
	<img
		src="https://http.cat/{$page.status}"
		class="w-full"
		alt="A cat representing the HTTP error code {$page.status}"
	/>
</div>

<style>
	.error {
		height: 100%;
		display: grid;
		place-content: center;
	}
</style>
