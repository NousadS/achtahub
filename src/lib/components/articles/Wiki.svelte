<script lang="ts">
    import Article from "./Article.svelte";

    // ── Data ──────────────────────────────────────────────────────────

    const faqs = [
        {
            q: "How do I claim land?",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua, ut enim ad minim.",
        },
        {
            q: "Are there any donator ranks?",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        },
        {
            q: "Can I play on Bedrock with Java players?",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.",
        },
        {
            q: "How do I report a player?",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore.",
        },
        {
            q: "Are mods allowed?",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia.",
        },
    ];

    const guides = [
        {
            q: "Getting Started: Your First Day",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua, ut enim ad minim.",
        },
        {
            q: "Economy & Trading Guide",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi aliquip.",
        },
        {
            q: "Land Claims & Permissions",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum.",
        },
        {
            q: "PvP Arena Rules & Ranking",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sunt in culpa qui officia deserunt mollit anim id est laborum lorem.",
        },
        {
            q: "Staff Application Process",
            a: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut labore et dolore magna aliqua enim ad minim veniam quis nostrud.",
        },
    ];

    // ── State ─────────────────────────────────────────────────────────
    let openFaq = null;
    let openGuide = null;

    function toggleFaq(i) {
        openFaq = openFaq === i ? null : i;
    }
    function toggleGuide(i) {
        openGuide = openGuide === i ? null : i;
    }
</script>

<Article
    id="wiki"
    step="5"
    label="Wiki"
    title="Guides & FAQ"
    description={`Frequently asked questions and beginner guides to help you get the most
        out of 8A HvGG.`}
>
    <div class="wiki-cols">
        <div>
            <div class="wiki-section-title">❓ FAQ</div>
            {#each faqs as f, i}
                <div class="accordion-item" class:open={openFaq === i}>
                    <button
                        class="accordion-head"
                        on:click={() => toggleFaq(i)}
                    >
                        {f.q}<span class="accordion-arrow">▼</span>
                    </button>
                    {#if openFaq === i}
                        <div class="accordion-body">{f.a}</div>
                    {/if}
                </div>
            {/each}
        </div>

        <div>
            <div class="wiki-section-title">📖 Guides</div>
            {#each guides as g, i}
                <div class="accordion-item" class:open={openGuide === i}>
                    <button
                        class="accordion-head"
                        on:click={() => toggleGuide(i)}
                    >
                        {g.q}<span class="accordion-arrow">▼</span>
                    </button>
                    {#if openGuide === i}
                        <div class="accordion-body">{g.a}</div>
                    {/if}
                </div>
            {/each}
        </div>
    </div>
</Article>

<style>
    /* ── WIKI ─────────────────────────────────────────────────────── */
    .wiki-cols {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1.5rem;
    }
    @media (max-width: 640px) {
        .wiki-cols {
            grid-template-columns: 1fr;
        }
    }
    .wiki-section-title {
        font-weight: 700;
        font-size: 0.95rem;
        margin-bottom: 0.75rem;
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }
    .accordion-item {
        border: 1px solid var(--stone-mid);
        border-radius: 10px;
        background: var(--white);
        margin-bottom: 0.5rem;
        overflow: hidden;
    }
    .accordion-head {
        width: 100%;
        background: none;
        border: none;
        padding: 0.8rem 1.1rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
        cursor: pointer;
        font-size: 0.875rem;
        font-weight: 600;
        color: var(--text);
        font-family: "Inter", sans-serif;
        text-align: left;
    }
    .accordion-head:hover {
        background: var(--stone-light);
    }
    .accordion-arrow {
        font-size: 0.75rem;
        color: var(--muted);
        transition: transform 0.15s;
    }
    .accordion-item.open .accordion-arrow {
        transform: rotate(180deg);
    }
    .accordion-body {
        padding: 0.1rem 1.1rem 0.9rem;
        font-size: 0.83rem;
        color: var(--muted);
        line-height: 1.6;
    }
</style>
