<script lang="ts">

</script>

<header id="header">
    <nav>
        <li>
            <a href="/">Overgrown</a>
        </li>
    </nav>
</header>

<main id="content">
    <slot></slot>
</main>

<footer id="footer">
    <div class="left"></div>
    <div class="right"></div>
</footer>

<style>
    #header, #content, #footer {
        display: grid;
    }

    #header {
        background-color: var(--og-color-lgreen);
        box-shadow: 0 0 10px 1px black;
        border-radius: 0 0 var(--normal-spacing) var(--normal-spacing);
    }

    #footer {
        grid-template: 'left . right' 100% / 1fr 2fr 1fr;

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