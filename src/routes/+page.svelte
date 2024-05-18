<script lang="ts">
    import sky from "$lib/assets/home-parallax/og-parallax-sky.png";
    import cloudsBack from "$lib/assets/home-parallax/og-parallax-clouds-back.png";
    import cloudsMiddle from "$lib/assets/home-parallax/og-parallax-clouds-middle.png";
    import cloudsMiddleFront from "$lib/assets/home-parallax/og-parallax-clouds-middle-front.png";
    import cloudsFront from "$lib/assets/home-parallax/og-parallax-clouds-front.png";
    import ChapterSleeve from "$lib/components/ChapterSleeve.svelte";

    const chapter = {
        id: 9,
        title: "TITRE DU CHAPITRE 9",
        image: "https://images.unsplash.com/photo-1616892488352-3581f2b56646?q=80&w=1886&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
        summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG",
        releaseDate: new Date(),
    };
</script>

<section class="parallax">
    <img class="sky" src={sky} alt="sky" />
    <img class="clouds-back" src={cloudsBack} alt="sky" />
    <img class="clouds-middle" src={cloudsMiddle} alt="sky" />
    <img class="clouds-middle-front" src={cloudsMiddleFront} alt="sky" />
    <img class="clouds-front" src={cloudsFront} alt="sky" />
    <div class="last-chapter _glass">
        <ChapterSleeve {chapter} isSelected></ChapterSleeve>
        <div class="title"></div>
    </div>
</section>

<style>
    .parallax {
        display: grid;
        align-items: end;
        grid-template: 100% / 100%;

        & > img {
            width: 100%;
        }

        & > .last-chapter {
            aspect-ratio: 4 / 2;
            display: grid;
            grid-template-columns: 40% 1fr;
            place-items: center;
            height: 50%;
            margin-inline: auto;
            margin-bottom: 30%;
            padding-inline: 2rem;
            border-radius: var(--normal-radius);
        }

        & > * {
            grid-area: 1 / 1;
            animation: parallax linear;
            animation-timeline: scroll();
        }

        & > .clouds-back {
            --parallax-speed: -5;
        }

        & > .clouds-middle {
            --parallax-speed: -10;
        }

        & > .clouds-middle-front {
            --parallax-speed: -15;
        }

        & > .clouds-front {
            --parallax-speed: -20;
        }
    }
</style>
