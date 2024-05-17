<script lang="ts">
</script>

<header id="header">
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
    #content,
    #footer {
        display: grid;
    }

    #header {
        position: sticky;
        top: 0;
        display: grid;
        grid-template: "home . navigation" 100% / auto 1fr auto;
        align-items: center;
        padding-inline: var(--larger-spacing);
        box-shadow: 0 0 10px 1px black;
        background-color: var(--og-color-lgreen);
        border-radius: 0 0 var(--normal-spacing) var(--normal-spacing);
        font-size: x-large;
    }

    .home {
        grid-area: home;
    }

    .navigation {
        grid-area: navigation;
    }

    #footer {
        grid-template: "left . right" 100% / 1fr 2fr 1fr;

        & > .left {
            grid-area: left;
            box-shadow: 0 0 10px 1px black;
            background-color: var(--og-color-lgreen);
            border-top-right-radius: var(--normal-spacing);
        }

        & > .right {
            grid-area: right;
            box-shadow: 0 0 10px 1px black;
            background-color: var(--og-color-lgreen);
            border-top-left-radius: var(--normal-spacing);
        }
    }
</style>
