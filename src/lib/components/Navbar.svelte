<script lang="ts">
	import Icon from '@iconify/svelte';
	import { slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	let isNavOpen = false;
</script>

{#if isNavOpen}
	<div
		role="presentation"
		class="absolute left-0 top-0 z-20 h-full w-full bg-black opacity-65"
		on:click={() => (isNavOpen = false)}
		on:scroll={() => (isNavOpen = false)}
	></div>
{/if}
{#if isNavOpen}
	<ul
		transition:slide={{ delay: 100, duration: 200, easing: quintOut, axis: 'x' }}
		class="menu menu-sm absolute left-[1rem] top-[3.8rem] z-30 mt-3 w-40 rounded-btn bg-base-100 p-2 shadow"
	>
		<li>
			<a on:click={() => (isNavOpen = false)} href="#home">Home</a>
		</li>
		<li>
			<a on:click={() => (isNavOpen = false)} href="#about">About</a>
		</li>
		<li>
			<a on:click={() => (isNavOpen = false)} href="#skills">Skills</a>
		</li>
		<li>
			<a on:click={() => (isNavOpen = false)} href="#services">Services</a>
		</li>
		<li>
			<a on:click={() => (isNavOpen = false)} href="#reviews">Reviews</a>
		</li>
	</ul>
{/if}
<nav class="navbar fixed left-0 top-0 z-10 bg-base-100 shadow-2xl">
	<div class="navbar-start">
		<div class="dropdown">
			<button
				tabindex="0"
				class="btn btn-ghost relative hidden lg:block"
				on:click={() => {
					isNavOpen = !isNavOpen;
				}}
			>
				{#if isNavOpen}
					<Icon icon="fontisto:close-a" />
				{:else}
					<Icon class="open" icon="pajamas:hamburger" />
				{/if}
			</button>
		</div>
		<a href="#home" class="pl-2 text-xl font-semibold lg:pl-4">TonyStar</a>
	</div>
	<div class="navbar-center flex lg:hidden">
		<ul class="flex gap-8">
			<li>
				<a class=" nav-links" href="#home">Home</a>
			</li>
			<li>
				<a class=" nav-links" href="#about">About</a>
			</li>
			<li>
				<a class=" nav-links" href="#skills">Skills</a>
			</li>
			<li>
				<a class=" nav-links" href="#services">Services</a>
			</li>
			<li>
				<a class=" nav-links" href="#reviews">Reviews</a>
			</li>
		</ul>
	</div>
	<div class="navbar-end pr-2">
		<a href="#contact" class="btn btn-primary btn-sm">Contact</a>
	</div>
</nav>
