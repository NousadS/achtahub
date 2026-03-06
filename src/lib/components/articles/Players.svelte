<script>
    import { fly } from "svelte/transition";
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
    const players = [
        {
            emoji: "🧑‍💻",
            name: "Notchify",
            role: "Admin",
            online: true,
            joined: "Jan 2022",
            playtime: "4,200 h",
            builds: 312,
            kills: 88,
            bio: "Server founder and head admin. Loves megabuilds and redstone contraptions.",
        },
        {
            emoji: "🧙",
            name: "WizardOak",
            role: "Moderator",
            online: true,
            joined: "Mar 2022",
            playtime: "2,100 h",
            builds: 198,
            kills: 542,
            bio: "PvP specialist and community event organiser.",
        },
        {
            emoji: "🏗",
            name: "Bricksworth",
            role: "Builder",
            online: false,
            joined: "Jul 2022",
            playtime: "1,850 h",
            builds: 520,
            kills: 12,
            bio: "Awarded Builder of the Month three times. Medieval style enthusiast.",
        },
        {
            emoji: "🌿",
            name: "FernGully",
            role: "Player",
            online: true,
            joined: "Dec 2022",
            playtime: "980 h",
            builds: 74,
            kills: 203,
            bio: "Nature-themed builder and active economy trader.",
        },
        {
            emoji: "⚡",
            name: "ZapRunner",
            role: "Player",
            online: false,
            joined: "Feb 2023",
            playtime: "660 h",
            builds: 45,
            kills: 1200,
            bio: "Top PvP arena champion for two seasons running.",
        },
        {
            emoji: "🎨",
            name: "Palettia",
            role: "Builder",
            online: true,
            joined: "May 2023",
            playtime: "740 h",
            builds: 290,
            kills: 3,
            bio: "Pixel art expert and creative world contributor.",
        },
        {
            emoji: "🧭",
            name: "ExplorerVex",
            role: "Player",
            online: false,
            joined: "Aug 2023",
            playtime: "430 h",
            builds: 30,
            kills: 60,
            bio: "Has discovered every biome on the SMP map. Cartography nerd.",
        },
        {
            emoji: "🐉",
            name: "Dracoveil",
            role: "Player",
            online: true,
            joined: "Nov 2023",
            playtime: "380 h",
            builds: 55,
            kills: 890,
            bio: "Dragon-lore fan and self-declared dungeon boss.",
        },
    ];
    let selectedPlayer = null;

    function openModal(p) {
        selectedPlayer = p;
    }
    function closeModal() {
        selectedPlayer = null;
    }
    function closeOnOverlay(e) {
        if (e.target === e.currentTarget) closeModal();
    }
</script>

<Article
    id="players"
    step="4"
    label="Players"
    title="Community Members"
    description={`Click any card to view a player's profile, stats, and join date.`}
>
    <div class="players-grid">
        {#each players as p, i}
            <button
                class="card player-card"
                on:click={() =>
                    openModal({ ...p, tint: TINTS[i % TINTS.length] })}
            >
                <div class="player-avatar {TINTS[i % TINTS.length]}">
                    {p.emoji}
                </div>
                <div class="player-name">{p.name}</div>
                <div class="player-role">
                    <span class="player-online {p.online ? 'on' : 'off'}"
                    ></span>{p.role}
                </div>
            </button>
        {/each}
    </div>

    <!-- ── PLAYER MODAL ───────────────────────────────────────────────── -->
    {#if selectedPlayer}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div
            class="modal-overlay open"
            on:click={closeOnOverlay}
            in:fly={{ delay: 100, duration: 250, x: -50, opacity: 0 }}
            out:fly={{ duration: 250, x: 50, opacity: 0 }}
        >
            <div class="modal">
                <button class="modal-close" on:click={closeModal}>✕</button>
                <div class="modal-avatar {selectedPlayer.tint}">
                    {selectedPlayer.emoji}
                </div>
                <h3>{selectedPlayer.name}</h3>
                <div class="modal-role">
                    <span
                        class="player-online {selectedPlayer.online
                            ? 'on'
                            : 'off'}"
                    ></span>
                    {selectedPlayer.role} ·
                    <!-- {#if selectedPlayer.online}       -->
                    {#if true}
                        <span class="online-text">Online now</span>
                    {:else}
                        Offline
                    {/if}
                </div>
                <p class="modal-bio">{selectedPlayer.bio}</p>
                <div class="stat-grid">
                    <div class="stat-box">
                        <div class="s-label">Joined</div>
                        <div class="s-val">{selectedPlayer.joined}</div>
                    </div>
                    <div class="stat-box">
                        <div class="s-label">Playtime</div>
                        <div class="s-val">{selectedPlayer.playtime}</div>
                    </div>
                    <div class="stat-box">
                        <div class="s-label">Builds</div>
                        <div class="s-val">{selectedPlayer.builds}</div>
                    </div>
                    <div class="stat-box">
                        <div class="s-label">PvP Kills</div>
                        <div class="s-val">{selectedPlayer.kills}</div>
                    </div>
                </div>
            </div>
        </div>
    {/if}
</Article>

<style>
    /* ── PLAYERS ──────────────────────────────────────────────────── */
    .players-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
        gap: 0.85rem;
    }
    .player-card {
        border-radius: var(--radius);
        padding: 1.25rem 1rem;
        text-align: center;
        cursor: pointer;
        background: var(--white);
        border: 1px solid var(--stone-mid);
        box-shadow: var(--shadow);
        font-family: "Inter", sans-serif;

        transition:
            0.3s transform ease,
            0.3s box-shadow ease,
            0.3s background ease,
            0.3s border ease;
    }
    .player-card:hover {
        transform: translateY(-5%);
        box-shadow: 0px 10px 5px var(--stone-mid);
        border-color: var(--green-mid);
    }
    .player-avatar {
        width: 56px;
        height: 56px;
        border-radius: 10px;
        margin: 0 auto 0.75rem;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.8rem;
        border: 2px solid var(--stone-mid);
    }
    .player-name {
        font-weight: 700;
        font-size: 0.95rem;
    }
    .player-role {
        font-size: 0.75rem;
        color: var(--muted);
        margin-top: 2px;
    }
    .player-online {
        display: inline-block;
        width: 7px;
        height: 7px;
        border-radius: 50%;
        margin-right: 4px;
    }
    .player-online.on {
        background: var(--status-online);
    }
    .player-online.off {
        background: var(--status-offline);
    }

    /* ── MODAL ────────────────────────────────────────────────────── */
    .modal-overlay {
        display: none;
        position: fixed;
        top: -20dvh;
        left: -20dvh;
        right: -20dvh;
        bottom: -20dvh;
        background: var(--modal-overlay);
        z-index: 200;
        align-items: center;
        justify-content: center;
        padding: 1rem;
    }
    .modal-overlay.open {
        display: flex;
    }
    .modal {
        background: var(--white);
        border-radius: var(--radius);
        max-width: 420px;
        width: 100%;
        padding: 2rem;
        position: relative;
        box-shadow: var(--modal-shadow);
    }
    .modal-close {
        position: absolute;
        top: 1rem;
        right: 1rem;
        background: var(--stone-light);
        border: none;
        border-radius: 50%;
        width: 30px;
        height: 30px;
        cursor: pointer;
        font-size: 1rem;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--muted);
    }
    .modal-close:hover {
        background: var(--stone-mid);
    }
    .modal-avatar {
        width: 72px;
        height: 72px;
        border-radius: 14px;
        font-size: 2.5rem;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 2px solid var(--stone-mid);
        margin-bottom: 1rem;
    }
    .modal h3 {
        font-size: 1.25rem;
        font-weight: 800;
    }
    .modal-role {
        color: var(--muted);
        font-size: 0.85rem;
        margin-bottom: 0.75rem;
        display: flex;
        align-items: center;
        gap: 4px;
    }
    .online-text {
        color: var(--green-dark);
        font-weight: 700;
    }
    .modal-bio {
        font-size: 0.85rem;
        color: var(--muted);
        margin-bottom: 0.5rem;
    }
    .stat-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 0.6rem;
        margin-top: 0.75rem;
    }
    .stat-box {
        background: var(--stone-light);
        border-radius: 8px;
        padding: 0.6rem 0.9rem;
        border: 1px solid var(--stone-mid);
    }
    .s-label {
        font-size: 0.7rem;
        color: var(--muted);
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.8px;
    }
    .s-val {
        font-size: 1rem;
        font-weight: 700;
        margin-top: 1px;
    }
</style>
