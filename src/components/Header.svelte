<script lang="ts">
	export const name: string = 'Quinten O\'Neal';
    export const title: string = 'Sample Portfolio';
</script>

<header>
    <h1>{name}</h1>
    <p>{title}</p>
</header>

<style>
    header {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        padding: 24px;
        z-index: 1;

        /* invert text */
        color: #ffffff;
        mix-blend-mode: difference;
    }

    h1 {
        font-variation-settings: "wght" 600;
	}
</style>