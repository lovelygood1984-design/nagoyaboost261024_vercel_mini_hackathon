<script lang="ts">
	import '../app.css';
	import { page } from '$app/state';

	let { children } = $props();

	const nav = [
		{ href: '/', label: 'おみくじ' },
		{ href: '/history', label: 'おみくじ記録' }
	];

	const centerImage =
		'https://xvmtct0eugcs16fs.public.blob.vercel-storage.com/omikuji_image/Hockey_Goal_Celebration.gif';
</script>

<div class="shell">
	<header>
		<a class="brand" href="/">⛩ おみくじ</a>
		<nav>
			{#each nav as item (item.href)}
				<a href={item.href} aria-current={page.url.pathname === item.href ? 'page' : undefined}>
					{item.label}
				</a>
			{/each}
		</nav>
	</header>

	<main>
		<div class="center-image">
			<img src={centerImage} alt="Hockey Goal Celebration" />
		</div>

		{@render children()}
	</main>

	<footer>SvelteKit + Vercel / SSR</footer>
</div>

<style>
	.shell {
		max-width: 42rem;
		margin: 0 auto;
		padding: 1.5rem 1rem 3rem;
		min-height: 100dvh;
		display: flex;
		flex-direction: column;
	}

	header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
		flex-wrap: wrap;
		padding-bottom: 1rem;
		border-bottom: 1px solid var(--line);
	}

	.brand {
		font-weight: 700;
		font-size: 1.1rem;
		text-decoration: none;
		color: var(--fg);
	}

	nav {
		display: flex;
		gap: 0.5rem;
	}

	nav a {
		padding: 0.35rem 0.75rem;
		border-radius: 999px;
		text-decoration: none;
		color: var(--muted);
		font-size: 0.9rem;
	}

	nav a[aria-current='page'] {
		background: var(--accent);
		color: #fff;
	}

	main {
		flex: 1;
		padding-top: 1.5rem;
	}

	.center-image {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 1.5rem 0 2rem;
	}

	.center-image img {
		max-width: 100%;
		width: 320px;
		height: auto;
		border-radius: 12px;
		display: block;
	}

	footer {
		padding-top: 2rem;
		font-size: 0.75rem;
		color: var(--muted);
		text-align: center;
	}
</style>
