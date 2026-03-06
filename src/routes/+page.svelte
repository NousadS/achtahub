<script>
    import Features from "$lib/components/articles/Features.svelte";
    import Players from "$lib/components/articles/Players.svelte";
    import Rules from "$lib/components/articles/Rules.svelte";
    import Start from "$lib/components/articles/Start.svelte";
    import Wiki from "$lib/components/articles/Wiki.svelte";
    import Footer from "$lib/components/common/Footer.svelte";
    import Menu from "$lib/components/common/Menu.svelte";
    import Hero from "$lib/components/common/Hero.svelte";
    import Divider from "$lib/components/common/Divider.svelte";
</script>

<Hero />
<Menu />
<div class="separator"></div>
<Start />
<Divider />
<Features />
<Divider />
<Rules />
<Divider />
<Players />
<Divider />
<Wiki />
<Divider />
<Footer />

<style>
    :global(.card) {
        background: var(--white);
        border: 1px solid var(--stone-mid);
        border-radius: var(--radius);
        box-shadow: var(--shadow);
    }

    .separator {
        height: 12dvh;
    }
</style>
