<script lang="ts">
    import type { Snippet } from "svelte";

    let {
        id,
        step,
        label,
        title,
        description,
        children,
    }: {
        id: string;
        step: string;
        label: string;
        title: string;
        description: string;
        children: Snippet;
    } = $props();
</script>

<section {id}>
    <p class="label">
        {step.padStart(2, "0")} &CenterDot; {label}
    </p>

    <h2 class="title">
        {title}
    </h2>

    <p class="description">
        {description}
    </p>

    {@render children()}
</section>

<style lang="scss">
    section {
        padding: 3.5rem 0;
        max-width: 1000px;
        margin: 0 auto;

        @media (max-width: 1000px) {
            & {
                padding: none;
                max-width: 600px;
            }
        }

        @media (max-width: 600px) {
            & {
                padding: none;
                max-width: 300px;
            }
        }

        .label {
            font-family: var(--font-caption);
            font-size: 0.8rem;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--green-dark);
            margin-bottom: 0.5rem;
        }

        .title {
            font-size: 1.6rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            margin-bottom: 0.35rem;
        }

        .description {
            color: var(--muted);
            font-size: 0.925rem;
            margin-bottom: 2rem;
        }
    }
</style>
