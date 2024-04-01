<script lang="ts">
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

<div class="editor">
  <h2>Archipelago connection</h2>
  <form class="ap-form"></form>

  <h2>Priority items</h2>
  <textarea bind:value={priorityTextBox} />
  <button on:click={updatePriorityItems}>Update</button>

  <h2>Normal items</h2>
  <textarea bind:value={normalTextBox} />
  <button on:click={updateNormalItems}>Update</button>
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
