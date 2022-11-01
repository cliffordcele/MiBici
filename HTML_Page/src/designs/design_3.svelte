<!-- Visualization based on: https://www.prcweb.co.uk/lab/circularheat/ -->


<script>
    // Size and margins
    const width = 600;
    const height = 250;
    const margin = { top: 10, right: 10, bottom: 10, left: 10 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // External libraries
    import { json } from "d3-fetch";
    import { onMount } from "svelte";
  
    // Import components
    import CircularHM from './design_3_CircularHM.svelte';
  
    // Name variables
    let data = null;
  
    // Load data
    //onMount(async () => {
      // Load full datatset
    //  data = await json("/data/hourly_heating_december.json");
    //});
  
  
    // Selects city dataset & scaling for plot based on radio buttons
    //$: apply_update(city_selected, scale_selected)
    //function apply_update(city_selected, scale_selected){
    //  console.log('update')
  </script>

  
 <!-- {#if !data}
    <p>Loading the data, please wait...</p>
  {:else}
    <div>
      <CircularHM data={data}/> 
    </div>
  {/if}-->








{#if !data}
  <p>Loading the data, please wait...</p>
{:else}
    <CircularHM data = {Balitmore_monthly_data} max_val = {max_value} graph_name = "Baltimore"/>
    <CircularHM data = {Chicago_monthly_data} max_val = {max_value} graph_name = "Chicago"/>
    <CircularHM data = {LA_monthly_data} max_val = {max_value} graph_name = "Los Angeles"/>
    <CircularHM data = {LA_monthly_data} max_val = {max_value} graph_name = "Los Angeles"/>
    {/if}
