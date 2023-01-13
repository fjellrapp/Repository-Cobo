<script>
	import { Button, ButtonTypeEnum, Dropdown } from 'cobo-ui';
	import { user } from '$lib/stores/user_store';
</script>

<div class="flex w-full justify-end p-4">
	<Button componentType={ButtonTypeEnum.PLAIN}>
		<span class=" text-black">
			{$user.user?.firstName ?? 'loading'}
		</span>
		<Dropdown label={$user.user?.firstName} labelColor="text-black" />
	</Button>
</div>
