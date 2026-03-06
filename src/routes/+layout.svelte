<script lang="ts">
    // Assets

    import "../app.scss";

    // Content

    import type { Snippet } from "svelte";

    let { children }: { children: Snippet } = $props();
</script>

{@render children()}