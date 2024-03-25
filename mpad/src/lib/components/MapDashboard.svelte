<script lang="ts">
    import { onDestroy, onMount, setContext,  } from 'svelte';
    import 'leaflet/dist/leaflet.css'
	import L from 'leaflet';
	
    export let bounds: L.LatLngBoundsExpression | undefined = undefined;
	export let view: L.LatLngExpression | undefined = undefined;
	export let zoom: number | undefined = undefined;

    let map: L.Map | undefined;
    let mapElement: HTMLDivElement;

    onMount(() => {
    map = L.map(mapElement);
    console.log('the component has mounted');
    
    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(map);

    })

    onDestroy(() => {
        map?.remove();
        map = undefined;
    });

    setContext('map', {
        getMap: () => map
    });
    
    $: if (map) {
        if (bounds) {
            map.fitBounds(bounds)
        } else if (view && zoom) {
            map.setView(view,zoom);
        }
    }
</script>


<div class="w-full h-full" bind:this={mapElement}>
    {#if map}
        <slot />
    {/if}
</div>
<!-- 
var map = L.map('map',{zoomControl: false ,center: new L.latLng([15.893333, 122.328331]),attributionControl: false}).setView([15.893333, 122.328331], 7);
        
        var markersLayer = new L.LayerGroup();
        map.addLayer(markersLayer);
        
        var layer = L.esri.basemapLayer('ImageryFirefly').addTo(map);
        var controlSearch = new L.Control.Search({
            position:'topleft',		
            layer: markersLayer,
            initial: false,
            zoom: 15,
            marker: false
        });
        
        

        map.addControl( controlSearch ); -->