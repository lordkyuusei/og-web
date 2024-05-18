<script lang="ts">
</script>

<header id="header" class="_glass">
    <nav class="home">
        <li>
            <a href="/">Overgrown</a>
        </li>
    </nav>
    <nav class="navigation">
        <li>
            <a href="/chapters">Chapters</a>
        </li>
    </nav>
</header>

<main id="content">
    <slot></slot>
</main>

<style>
    #header,
    #content {
        display: grid;
    }

    #header {
        z-index: 2;
        height: 10svh;
        position: sticky;
        top: 0;
        width: 100%;
        grid-template: "home . navigation" 100% / auto 1fr auto;
        align-items: center;
        padding-inline: var(--larger-spacing);
        border-radius: 0 0 var(--normal-spacing) var(--normal-spacing);
        font-size: x-large;

        & > .home {
            grid-area: home;
        }

        & > .navigation {
            grid-area: navigation;
        }
    }

    #content {
        height: 100%;
    }
</style>
