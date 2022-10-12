<script>
  export let tag = '';
  export let active = false;

  import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
</script>

<span class="tag {active && 'active'}" on:click={() => dispatch('click', tag)}>{tag}</span>

<style>
  .tag {
    font-size: 12px;
    border: 1px solid #CCC;
    line-height: 1.4;
    padding: 0 4px;
    border-radius: 2px;
    cursor: pointer;
  }

  .active {
    background-color: #CCC;
    color: #232323;
  }
</style>