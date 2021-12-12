<script lang="ts">
    export let src: string = '';
    export let title: string = '';
</script>

<section>
    <img {src} alt={title} />
</section>

<style>
    section {
        background: var(--page-back);
        padding: var(--section-pad);
        height: var(--section-height);

        display: flex;
        align-items: center;
        justify-content: center;

        border-bottom: 1px solid var(--section-border);
    }

    section img {
        object-fit: contain;
        max-width: 100%;
        max-height: 100%;
    }
</style>