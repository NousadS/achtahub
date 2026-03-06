<script lang="ts">
    const items: Array<{ name: string; url: string }> = [
        { name: "Start", url: "#start" },
        { name: "Features", url: "#features" },
        { name: "Rules", url: "#rules" },
        { name: "Players", url: "#players" },
        { name: "Wiki", url: "#wiki" },
    ];

    let scrolled: number = $state(0);
    let lastScrolled: number = $state(0);
    let locking: boolean = $state(false);

    function onscroll(_: UIEvent) {
        lastScrolled = scrolled;
        scrolled = Math.min(1, window.scrollY / window.innerHeight);

        const scrollingDown = scrolled > lastScrolled;
        const nearTop = scrolled < 0.25;

        if (nearTop && scrollingDown && !locking) {
            locking = true;

            window.scrollTo(0, window.innerHeight);

            setTimeout(() => (locking = false), 900);
        }

        if (locking) _.preventDefault();
    }
</script>

<svelte:window {onscroll} />

<nav style:--scrolled={scrolled}>
    <ul>
        {#each items.slice(0, Math.floor(items.length / 2)) as item}
            <li><a href={item.url}>{item.name}</a></li>
        {/each}
    </ul>

    <a class="logo" href="#hero">
        <img src="/favicon.png" alt="A minecraft server logo." />
    </a>

    <ul>
        {#each items.slice(Math.floor(items.length / 2)) as item}
            <li><a href={item.url}>{item.name}</a></li>
        {/each}
    </ul>
</nav>

<style lang="scss">
    nav {
        --scrolled: 0;

        position: fixed;
        top: calc((100dvh - 12dvh) / 2 * (1 - var(--scrolled)));
        left: 0;
        right: 0;

        padding: 0 2rem;
        height: 12dvh;
        z-index: 100;

        background: hsla(
            from var(--white) h s l / calc(var(--scrolled) * 100%)
        );
        backdrop-filter: blur(calc(15px * var(--scrolled)));
        border-bottom: 1px solid
            hsla(from var(--stone-mid) h s l / calc(var(--scrolled) * 100%));

        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-direction: row;
        flex-wrap: nowrap;
    }

    ul {
        display: flex;
        align-items: center;
        justify-content: space-around;
        flex-direction: row;
        flex-wrap: nowrap;
        gap: 2rem;
        list-style: none;
        width: 40dvw;

        @media (max-width: 780px) {
            * {
                display: none;
                width: 0dvw;
                height: 0dvh;
            }
        }
    }

    nav ul li {
        width: 33%;
        height: 100%;
    }

    nav ul li a {
        display: flex;
        align-items: center;
        justify-content: center;

        color: var(--muted);
        text-decoration: none;
        font-size: 0.9rem;
        font-weight: 500;

        opacity: var(--scrolled);
        transition: color 0.3s;
    }

    nav ul li a:hover {
        color: var(--green-dark);
    }

    nav .logo img {
        height: calc(20dvh - 10dvh * var(--scrolled));
        aspect-ratio: 1 / 1;
    }

    .logo {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: transform 0.3s;
    }

    .logo:hover {
        transform: scale(0.9);
        transition: transform 0.2s;
    }

    .logo:active {
        transform: scale(0.5);
    }
</style>
