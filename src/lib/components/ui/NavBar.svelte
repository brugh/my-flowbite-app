<script lang="ts">
	import { page } from '$app/stores';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';

	interface Nav {
		href: string;
		desc: string;
	}

	const navs: Nav[] = [
		{ href: '/', desc: 'Home' },
		{ href: '/about', desc: 'About' },
		{ href: '/services', desc: 'Services' },
		{ href: '/contact', desc: 'Contact' }
	];
</script>

<Navbar let:hidden let:toggle>
	<NavBrand href="/">
		<img src="/favicon.png" class="mr-3 h-6 sm:h-9" alt="Flowbite Logo" />
		<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
			Flowbite
		</span>
	</NavBrand>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden} on:click={toggle}>
		{#each navs as nav}
			<NavLi active={$page.url.pathname === nav.href} href={nav.href}>
				{nav.desc}
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- <span on:click|preventDefault={toggle}>{nav.desc}</span> -->
			</NavLi>
		{/each}
		<!-- <NavLi href="/" active={true}>Home</NavLi>
    <NavLi href="/about">About</NavLi>
    <NavLi href="/services">Services</NavLi>
    <NavLi href="/pricing">Pricing</NavLi>
    <NavLi href="/contact">Contact</NavLi> -->
	</NavUl>
</Navbar>
