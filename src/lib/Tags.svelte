<script>
    import Tag from './Tag.svelte';
    export let tags = [];
    export let activeTags = [];

    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

    function handleClick(tag) {
        dispatch('click', tag)
    }
</script>

<div class="tags">
    {#each tags as tag}
        {#if activeTags.includes(tag)}
            <Tag tag={tag} active={true} on:click={handleClick} />
        {:else}
            <Tag tag={tag} active={false} on:click={handleClick} />
        {/if}
    {/each}
</div>

<style>
    .tags {
        display: flex;
        gap: 10px;
    }
</style>