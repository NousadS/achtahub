<script lang="ts">
    let scrolled: number = $state(0);

    function onscroll(_: UIEvent) {
        scrolled = Math.min(1, (window.scrollY / window.innerHeight) * 4);
    }
</script>

<svelte:window {onscroll} />

<header id="hero" style:--scrolled={scrolled}>
    <div class="grid"></div>

    <div class="top">
        <div class="badge">
            <span class="dot"></span> Server Online — 1.21.11
        </div>
        <h1>Welcome to <em>Server 8a HvGG</em></h1>
    </div>

    <hr />

    <p class="bottom">
        A survival community with no pay-to-win, no resets. <br />
        Just good people building great things.
    </p>
</header>

<style>
    header {
        --scrolled: 0;

        position: relative;
        height: 100dvh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        text-align: center;
        padding: 5rem 2rem 4rem;
        overflow: hidden;
        background: var(--bg);
        border-bottom: 1px solid var(--stone-mid);
    }

    header > * {
        opacity: calc(1 - var(--scrolled));
    }

    header hr {
        border: none;
        height: 15dvh;
        flex-shrink: 0;
    }

    /* ── Grid background ─────────────────────────────────────────── */
    .grid {
        position: absolute;
        inset: 0;
        background-image: linear-gradient(
                hsla(from var(--green) h s l / 7%) 1px,
                transparent 1px
            ),
            linear-gradient(
                90deg,
                hsla(from var(--green) h s l / 7%) 1px,
                transparent 1px
            );
        background-size: 40px 40px;
    }

    .grid::after {
        content: "";
        position: absolute;
        inset: 0;
        background: radial-gradient(
            ellipse 70% 60% at 50% 50%,
            transparent 30%,
            var(--bg) 100%
        );
    }

    /* ── Top block ───────────────────────────────────────────────── */
    .top {
        height: 40dvh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .badge {
        position: relative;
        z-index: 1;
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        background: hsla(from var(--green-dark) h s l / 0.1);
        border: 1px solid hsla(from var(--green-dark) h s l / 0.3);
        border-radius: 999px;
        padding: 0.35rem 1rem;
        font-size: 0.75rem;
        font-weight: 600;
        color: var(--green-dark);
        margin-bottom: 1.5rem;
    }

    .dot {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: var(--green-dark);
        flex-shrink: 0;
    }

    h1 {
        position: relative;
        z-index: 1;
        font-family: "Inter", sans-serif;
        font-size: clamp(1.2rem, 3.5vw, 2.2rem);
        font-weight: 800;
        letter-spacing: -0.5px;
        color: var(--text);
        line-height: 1.6;
        margin-bottom: 1rem;
    }

    h1 em {
        color: var(--green-dark);
        font-style: normal;
        font-family: var(--font-caption);
    }

    /* ── Bottom block ────────────────────────────────────────────── */
    .bottom {
        height: 40dvh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
        z-index: 1;
        color: var(--muted);
        max-width: 500px;
        font-size: 1rem;
        line-height: 1.7;
    }
</style>
