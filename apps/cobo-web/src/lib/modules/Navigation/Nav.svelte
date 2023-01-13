<script lang="ts">
	import { goto } from '$app/navigation';
	import { page } from '$app/stores';
	import { Button, ButtonTypeEnum, CogIcon, LoginIcon, SignupIcon, PlusIcon } from 'cobo-ui';
	import { user } from '$lib/stores/user_store';
	import Menu from './Menu.svelte';

	let authenticated = false;
	let activeRoute: string;
	let settingsPaneOpen = false;
	page.subscribe((p) => {
		if (p.route.id) {
			activeRoute = p.route.id;
		}
	});

	user.subscribe((store) => {
		authenticated = store.isAuthenticated;
	});
</script>

<div class="nav">
	<div class="logo">
		<h1 class=" text-xs font-extrabold uppercase">Cobo</h1>
	</div>
	{#if authenticated}
		<Menu />
	{:else}
		<div class="menu-auth">
			<Button
				iconOnly
				beforeIcon={LoginIcon}
				active={activeRoute === '/'}
				title="Logg inn"
				on:click={() => goto('/')}
			/>
			<Button
				iconOnly
				beforeIcon={SignupIcon}
				active={activeRoute === '/registrer'}
				title="Registrer deg"
				on:click={() => goto('/registrer')}
			/>
		</div>
	{/if}
	<div class="actions">
		{#if authenticated}
			<Button
				beforeIcon={PlusIcon}
				iconOnly
				active
				componentType={ButtonTypeEnum.SECONDARY}
				title="Legg til hendelse, aktivitet eller andre ting"
			/>
		{/if}
		<Button
			iconOnly
			beforeIcon={CogIcon}
			active={activeRoute === '/settings'}
			title="Innstillinger"
			on:click={() => {
				goto('/settings');
			}}
		/>
	</div>
</div>

<style>
	.nav {
		@apply gap-xs bg-primaryBg flex h-screen flex-col items-center justify-between p-3;
	}
	.actions {
		@apply flex flex-col gap-2;
	}
</style>
