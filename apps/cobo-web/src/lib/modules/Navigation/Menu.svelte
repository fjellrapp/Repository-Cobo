<script lang="ts">
	import { Button, BellIcon, ChartPieIcon, ClipboardIcon, HomeIcon } from 'cobo-ui';

	import { page } from '$app/stores';
	import { goto } from '$app/navigation';

	let activeRoute: string;
	page.subscribe((p) => {
		if (p.route.id) {
			activeRoute = p.route.id;
		}
	});
</script>

<div class="menu-items">
	<Button
		iconOnly
		beforeIcon={HomeIcon}
		title="Hjem"
		active={activeRoute === '/'}
		on:click={() => goto('/')}
	/>
	<Button
		iconOnly
		beforeIcon={ClipboardIcon}
		title="Gjøremål"
		active={activeRoute === '/activities'}
		on:click={() => goto('/activities')}
	/>
	<Button
		iconOnly
		beforeIcon={BellIcon}
		title="Påminnelser"
		active={activeRoute === '/reminders'}
		on:click={() => goto('/reminders')}
	/>
	<Button
		iconOnly
		beforeIcon={ChartPieIcon}
		title="Statistikk"
		active={activeRoute === '/statistics'}
		on:click={() => goto('/statistics')}
	/>
</div>

<style>
	.menu-items {
		@apply flex flex-col gap-2;
	}
</style>
