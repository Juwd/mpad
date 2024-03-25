<script lang=ts>
	import { AppShell,SlideToggle, } from "@skeletonlabs/skeleton";
	import type {LatLngExpression} from "leaflet"
	import MapDashboard from "$lib/components/MapDashboard.svelte";
	
	let LMPA: boolean = false;
	let NIPAS: boolean = true;
	const initialView: LatLngExpression = [15.893333, 122.328331];

</script>


<AppShell>
	<div class="h-full flex  space-y-8">
		<MapDashboard view={initialView} zoom={8} />
	</div>
	<svelte:fragment slot="pageFooter">
		<svelter:fragment slot="areas" class="flex pb-4 justify-center ">
			<SlideToggle name="slide" bind:checked={LMPA} > LMPA {LMPA ? 'show' : 'hide'} </SlideToggle>
			<SlideToggle name="slide" class="ml-2" bind:checked={NIPAS}>NIPAS {NIPAS ? 'show': 'hide'} </SlideToggle>	
		</svelter:fragment>

	</svelte:fragment>
</AppShell>