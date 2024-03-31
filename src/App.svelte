<script lang="ts">
  import svelteLogo from "./assets/svelte.svg";
  import viteLogo from "/vite.svg";
  import Counter from "./lib/Counter.svelte";

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
  {#each priorityItems as item}
    <div class="sidebar-item priority">{item}</div>
  {/each}
  {#each normalItems as item}
    <div class="sidebar-item">{item}</div>
  {/each}
</div>

<style>
</style>
