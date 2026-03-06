<script lang="ts">
    import Article from "./Article.svelte";

    const TINTS = [
        "tint-a",
        "tint-b",
        "tint-c",
        "tint-d",
        "tint-e",
        "tint-f",
        "tint-g",
        "tint-h",
    ];

    const features = [
        {
            icon: "🏔",
            title: "Survival SMP",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "🏙",
            title: "Creative World",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "⚔",
            title: "PvP Arenas",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "🤝",
            title: "Economy",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "🏡",
            title: "Land Claims",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "🎉",
            title: "Events",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "💬",
            title: "Discord Link",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
        {
            icon: "🗺",
            title: "Dynmap",
            desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit ut labore.",
        },
    ];
</script>

<Article
    id="features"
    step="2"
    label="Features"
    title="What We Offer"
    description={`Everything you need for an amazing Minecraft experience.`}
>
    <div class="features-grid">
        {#each features as f, i}
            <div class="feature-card {TINTS[i % TINTS.length]}">
                <div class="f-icon">{f.icon}</div>
                <div class="f-title">{f.title}</div>
                <div class="f-desc">{f.desc}</div>
            </div>
        {/each}
    </div>
</Article>

<style>
    /* ── FEATURES ─────────────────────────────────────────────────── */
    .features-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 0.85rem;
    }
    .feature-card {
        padding: 1.1rem 1.25rem;
        border-radius: var(--radius);
        border: 1px solid var(--stone-mid);
        box-shadow: var(--shadow);
        cursor: default;

        transition:
            0.3s transform ease,
            0.3s box-shadow ease,
            0.3s background ease,
            0.3s border ease;

        &:hover {
            transform: translateY(-5%);
            box-shadow: 0px 10px 5px var(--stone-mid);

            &.tint-a {
                border: 1px solid hsl(from var(--tint-a) h s calc(l - 20));
                background: hsl(from var(--tint-a) h calc(s - 2) calc(l - 5));
            }
            &.tint-b {
                border: 1px solid hsl(from var(--tint-b) h s calc(l - 20));
                background: hsl(from var(--tint-b) h calc(s - 2) calc(l - 5));
            }
            &.tint-c {
                border: 1px solid hsl(from var(--tint-c) h s calc(l - 20));
                background: hsl(from var(--tint-c) h calc(s - 2) calc(l - 5));
            }
            &.tint-d {
                border: 1px solid hsl(from var(--tint-d) h s calc(l - 20));
                background: hsl(from var(--tint-d) h calc(s - 2) calc(l - 5));
            }
            &.tint-e {
                border: 1px solid hsl(from var(--tint-e) h s calc(l - 20));
                background: hsl(from var(--tint-e) h calc(s - 2) calc(l - 5));
            }
            &.tint-f {
                border: 1px solid hsl(from var(--tint-f) h s calc(l - 20));
                background: hsl(from var(--tint-f) h calc(s - 2) calc(l - 5));
            }
            &.tint-g {
                border: 1px solid hsl(from var(--tint-g) h s calc(l - 20));
                background: hsl(from var(--tint-g) h calc(s - 2) calc(l - 5));
            }
            &.tint-h {
                border: 1px solid hsl(from var(--tint-h) h s calc(l - 20));
                background: hsl(from var(--tint-h) h calc(s - 2) calc(l - 5));
            }
        }
    }
    .f-icon {
        font-size: 1.6rem;
        margin-bottom: 0.5rem;
    }
    .f-title {
        font-weight: 700;
        font-size: 0.9rem;
        margin-bottom: 0.25rem;
    }
    .f-desc {
        font-size: 0.8rem;
        color: var(--muted);
        line-height: 1.5;
    }
</style>
