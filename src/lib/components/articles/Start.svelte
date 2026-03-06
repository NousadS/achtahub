<script lang="ts">
    import Article from "./Article.svelte";

    let copiedAddr = null;

    async function copyAddr(addr) {
        await navigator.clipboard.writeText(addr);
        copiedAddr = addr;
        setTimeout(() => (copiedAddr = null), 2000);
    }
</script>

<Article
    id="start"
    step="1"
    label="Getting Started"
    title="Join the Server"
    description="Join via Java or Bedrock — both editions are supported."
>
    <div class="start-grid">
        {#each [{ emoji: "☕", edition: "Java Edition", addr: "exaroton.me", port: "Port: 25565 (default)" }, { emoji: "🪨", edition: "Bedrock Edition", addr: "be.hvgg8a.net", port: "Port: 19132" }] as s}
            <div class="card addr-card">
                <div class="edition"><span>{s.emoji}</span>{s.edition}</div>
                <div class="addr-row">
                    <code>{s.addr}</code>
                    <button
                        class="copy-btn"
                        class:copied={copiedAddr === s.addr}
                        on:click={() => copyAddr(s.addr)}
                    >
                        {copiedAddr === s.addr ? "Copied!" : "Copy"}
                    </button>
                </div>
                <div class="sub">{s.port}</div>
            </div>
        {/each}
    </div>

    <div class="info-row">
        {#each [{ ic: "🟢", label: "Status", val: "Online" }, { ic: "📦", label: "Version", val: "1.21.11" }, { ic: "👥", label: "Players", val: "14 / 50" }, { ic: "⏱️", label: "Uptime", val: "99.8 %" }] as chip}
            <div class="info-chip">
                <span class="ic">{chip.ic}</span>
                <div>
                    <div class="ic-label">{chip.label}</div>
                    <div class="ic-val">{chip.val}</div>
                </div>
            </div>
        {/each}
    </div>
</Article>

<style lang="scss">
    .start-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
    }
    @media (max-width: 600px) {
        .start-grid {
            grid-template-columns: 1fr;
        }
    }
    .addr-card {
        padding: 1.25rem 1.5rem;
        transition:
            0.3s transform ease,
            0.3s box-shadow ease,
            0.3s border ease;

        &:hover {
            transform: translateY(-5%);
            box-shadow: 0px 10px 5px var(--stone-mid);
            border: 1px solid var(--border);
        }
    }
    .edition {
        font-size: 0.7rem;
        font-weight: 700;
        font-family: var(--font-caption);
        letter-spacing: 1.5px;
        text-transform: uppercase;
        color: var(--muted);
        margin-bottom: 0.4rem;

        span {
            font-family: var(--font);
        }
    }
    .addr-row {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        margin-bottom: 0.3rem;
    }
    .addr-card code {
        font-family: "JetBrains Mono", monospace;
        font-size: 0.95rem;
        font-weight: 600;
        background: var(--stone-light);
        padding: 3px 8px;
        border-radius: 6px;
    }
    .copy-btn {
        background: none;
        border: 1px solid var(--stone-mid);
        border-radius: 6px;
        padding: 3px 8px;
        font-size: 0.75rem;
        cursor: pointer;
        color: var(--muted);
        font-family: "Inter", sans-serif;
        font-weight: 500;
    }
    .copy-btn:hover {
        background: var(--stone-light);
        color: var(--text);
    }
    .copy-btn.copied {
        color: var(--green-dark);
        border-color: var(--green-mid);
    }
    .sub {
        font-size: 0.8rem;
        color: var(--muted);
        margin-top: 0.1rem;
    }
    .info-row {
        display: flex;
        gap: 1rem;
        margin-top: 1rem;
        flex-wrap: wrap;
    }
    .info-chip {
        display: flex;
        align-items: center;
        gap: 8px;
        background: var(--white);
        border: 1px solid var(--stone-mid);
        border-radius: 10px;
        padding: 0.75rem 1.25rem;
        flex: 1;
        min-width: 140px;
        box-shadow: var(--shadow);
        transition:
            0.3s transform ease,
            0.3s box-shadow ease,
            0.3s border ease;

        &:hover {
            transform: translateY(-5%);
            box-shadow: 0px 10px 5px var(--stone-mid);
            border: 1px solid var(--border);
        }
    }
    .ic {
        font-size: 1.4rem;
    }
    .ic-label {
        font-size: 0.7rem;
        color: var(--muted);
        font-family: var(--font-caption);
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: 600;
    }
    .ic-val {
        font-size: 0.95rem;
        font-weight: 700;
    }
</style>
