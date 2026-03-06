<script lang="ts">
    import Article from "./Article.svelte";
    const rules = [
        {
            num: "01",
            title: "No Griefing",
            severity: "high",
            desc: "Destroying or altering another player's builds without consent is strictly forbidden.",
            example:
                "Breaking blocks inside someone's house while they're offline.",
            punishment: "Immediate 7-day ban; permanent on second offence.",
        },
        {
            num: "02",
            title: "Respect All Players",
            severity: "mid",
            desc: "Harassment, hate speech, discrimination, or personal attacks will not be tolerated.",
            example:
                "Sending repeated unwanted messages or using slurs in chat.",
            punishment: "Mute → 3-day ban → permanent ban.",
        },
        {
            num: "03",
            title: "No Cheating or Hacking",
            severity: "high",
            desc: "Using modified clients, x-ray packs, or any exploit that gives unfair advantage.",
            example:
                "Flying without a legitimate game mode, speed-hacking in PvP.",
            punishment: "Permanent ban, no appeal.",
        },
        {
            num: "04",
            title: "No Spam or Advertising",
            severity: "low",
            desc: "Flooding chat with repeated messages or advertising other servers is not allowed.",
            example: "Posting the same message 5 times in 10 seconds.",
            punishment: "Warning → 1-hour mute → 24-hour mute.",
        },
        {
            num: "05",
            title: "No Excessive PvP Killing",
            severity: "low",
            desc: "Killing the same player repeatedly (camping) without consent outside arenas.",
            example: "Spawn-killing a new player more than twice in a row.",
            punishment: "Warning → 6-hour ban from PvP zones.",
        },
        {
            num: "06",
            title: "Follow Staff Instructions",
            severity: "mid",
            desc: "Staff decisions are final during incidents. Disputes can be raised on Discord after.",
            example:
                "Ignoring a moderator's request to move away from a contested area.",
            punishment: "Kick → 1-day ban → permanent ban.",
        },
    ];
</script>

<Article
    id="rules"
    step="3"
    label="Rules"
    title="Server Rules"
    description={`Violations are handled progressively. Severe breaches skip straight to
        permanent bans. Staff have final say.`}
>
    <div class="rules-list">
        {#each rules as r}
            <div class="rule-item severity-{r.severity}">
                <div class="rule-header">
                    <span class="rule-num">#{r.num}</span>
                    <span class="rule-title">{r.title}</span>
                </div>
                <div class="rule-desc">{r.desc}</div>
                <div class="rule-meta">
                    <span class="badge example">📌 {r.example}</span>
                    <span class="badge punishment">⚠ {r.punishment}</span>
                </div>
            </div>
        {/each}
    </div>
</Article>

<style>
    /* ── RULES ────────────────────────────────────────────────────── */
    .rules-list {
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
    }
    .rule-item {
        border-radius: var(--radius);
        padding: 1rem 1.25rem;
        background: var(--white);
        border: 1px solid var(--stone-mid);
        box-shadow: var(--shadow);
        border-left-width: 4px;
        border-left-style: solid;
    }
    .rule-item.severity-low {
        border-left-color: var(--severity-low);
    }
    .rule-item.severity-mid {
        border-left-color: var(--severity-mid);
    }
    .rule-item.severity-high {
        border-left-color: var(--severity-high);
    }
    .rule-header {
        display: flex;
        align-items: center;
        gap: 0.6rem;
        margin-bottom: 0.4rem;
    }
    .rule-num {
        background: var(--stone-light);
        border: 1px solid var(--stone-mid);
        border-radius: 6px;
        font-size: 0.75rem;
        font-weight: 700;
        color: var(--muted);
        padding: 1px 7px;
        font-family: "JetBrains Mono", monospace;
    }
    .rule-title {
        font-weight: 700;
        font-size: 0.95rem;
    }
    .rule-desc {
        font-size: 0.85rem;
        color: var(--muted);
        margin-bottom: 0.6rem;
    }
    .rule-meta {
        display: flex;
        gap: 0.5rem;
        flex-wrap: wrap;
    }
    .badge {
        font-size: 0.7rem;
        font-weight: 600;
        padding: 2px 8px;
        border-radius: 999px;
        display: inline-flex;
        align-items: center;
        gap: 4px;
    }
    .badge.example {
        background: var(--badge-example-bg);
        color: var(--badge-example-text);
        border: 1px solid var(--badge-example-border);
    }
    .badge.punishment {
        background: var(--badge-punish-bg);
        color: var(--badge-punish-text);
        border: 1px solid var(--badge-punish-border);
    }
</style>
