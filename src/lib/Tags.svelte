<script>
    import Tag from './Tag.svelte';
    export let tags = [];
</script>

<div class="tags">
    {#each tags as tag}
        <Tag tag={tag} />
    {/each}
</div>

<style>
    .tags {
        display: flex;
        gap: 10px;
    }
</style>