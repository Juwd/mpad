<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar, initializeStores, Drawer, getDrawerStore } from '@skeletonlabs/skeleton';
	import Navigation from '$lib/navigation/Navigation.svelte';
	
	// import { page } from '$app/stores';
	// // console.log($page.url.pathname)

	initializeStores();
	const drawerStore = getDrawerStore();
	
	function drawerOpen(): void {
	drawerStore.open({});
	}


</script>

<!-- App Shell -->
<Drawer>
	<nav class="list-nav p-4">
		<Navigation />
	</nav>
</Drawer>
<AppShell slotSidebarLeft="bg-surface-500/5 w-0 lg:w-64">	
	<svelte:fragment slot="header">
		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
				<svelte:fragment slot="lead">
					<div class="flex items-center">
						<button class="btn btn-sm mr-4" on:click={drawerOpen}>
							<span>
								<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
									<rect width="100" height="20" />
									<rect y="30" width="100" height="20" />
									<rect y="60" width="100" height="20" />
								</svg>
							</span>
						</button>
						<strong class="text-xl uppercase">MSN</strong>
					</div>
				</svelte:fragment>
			<h1 class="h1">MPA Database</h1>
			<svelte:fragment slot="trail">(actions)</svelte:fragment>
		</AppBar>
	</svelte:fragment>



	<!-- Page Route Content -->
	<slot />
	
</AppShell>
