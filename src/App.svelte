<script lang="ts">
  import svelteLogo from "./assets/svelte.svg";
  import viteLogo from "/vite.svg";
  import Counter from "./lib/Counter.svelte";
  import { flip } from "svelte/animate";
  import { fade } from "svelte/transition";

  let priorityTextBox: string = "Item 1";
  let priorityTextSaved: string = priorityTextBox;
  $: priorityItems = priorityTextSaved.split("\n");

  let normalTextBox: string = "Item 2";
  let normalTextSaved: string = normalTextBox;
  $: normalItems = normalTextSaved.split("\n");

  function updatePriorityItems() {
    priorityTextSaved = priorityTextBox;
  }

  function updateNormalItems() {
    normalTextSaved = normalTextBox;
  }
</script>

<div class="editor" style="flex: 1">
  <h2>Priority items</h2>
  <textarea bind:value={priorityTextBox} />
  <button style="padding: 5px;" on:click={updatePriorityItems}>Update</button>

  <h2>Normal items</h2>
  <textarea bind:value={normalTextBox} />
  <button style="padding: 5px;" on:click={updateNormalItems}>Update</button>
</div>
<div class="right-column">
  <ul class="sidebar-items">
    {#each priorityItems as item (item)}
      <li transition:fade animate:flip class="priority-item">{item}</li>
    {/each}
    {#each normalItems as item (item)}
      <li transition:fade animate:flip class="normal-item">{item}</li>
    {/each}
  </ul>
</div>

<style>
</style>
