<script lang=ts>
	import { AppShell,SlideToggle, } from "@skeletonlabs/skeleton";

	let LMPA: boolean = false;
	let NIPAS: boolean = true;

</script>


<AppShell>
	<div class="container h-full flex  space-y-8">
		<h1 class="h1">Insert Map here</h1>
	</div>
	<svelte:fragment slot="pageFooter">
		<svelter:fragment slot="areas" class="flex pb-4 justify-center ">
			<SlideToggle name="slide" bind:checked={LMPA} > LMPA {LMPA ? 'show' : 'hide'} </SlideToggle>
			<SlideToggle name="slide" class="ml-2" bind:checked={NIPAS}>NIPAS {NIPAS ? 'show': 'hide'} </SlideToggle>	
		</svelter:fragment>

	</svelte:fragment>
</AppShell>