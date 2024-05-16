<script lang="ts">
    let chapters: any[] = [
        { id: 9, title: "TITRE DU CHAPITRE 9", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 8, title: "TITRE DU CHAPITRE 8", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 7, title: "TITRE DU CHAPITRE 7", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 6, title: "TITRE DU CHAPITRE 6", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 5, title: "TITRE DU CHAPITRE 5", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 4, title: "TITRE DU CHAPITRE 4", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 3, title: "TITRE DU CHAPITRE 3", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 2, title: "TITRE DU CHAPITRE 2", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 1, title: "TITRE DU CHAPITRE 1", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 0, title: "TITRE DU CHAPITRE 0", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
    ];

    let selectedChapter: number | null = chapters[0].id;
    let localizer: Intl.DateTimeFormat = new Intl.DateTimeFormat("fr", { dateStyle: "long" });
    let ref: HTMLUListElement;

    const selectChapter = (event: Event, chapter: any) => {
        selectedChapter = chapter.id;
        console.log(event);
        event.currentTarget.scrollIntoView({ behavior: "smooth", inline: "start", block: "start" })
    }
</script>

<ul>
    {#each chapters as chapter}
    <li class:selected={chapter.id === selectedChapter}>
        <button on:click={(event) => selectChapter(event, chapter)} class="chapter chapter-{chapter.id}" data-chapter-summary={chapter.summary}>
            <header class="title">{chapter.title}</header>
            {#if selectedChapter === chapter.id}
                <footer class="actions"><a href="/comic/{chapter.id}">Read chapter {chapter.id}</a></footer>
            {/if}
        </button>
    </li>
    {/each}
</ul>

<style>
    ul, li {
        padding: 0;
        margin: 0;
        list-style: none;
    }

    ul {
        display: flex;
        align-items: end;
        gap: 2rem;
        width: 100%;
        overflow-x: auto;

        scrollbar-width: 0;
        scroll-padding-inline-start: 30svw;
        padding-inline-start: 10svw;
    }

    li {
        min-width: 20%;
        transition: all 0.2s cubic-bezier(0.075, 0.82, 0.165, 1);
    }

    li.selected {
        min-width: min(40%, 40svw);
    }

    .chapter {
        display: grid;
        grid-template:
            'title' 1fr
            '.' 9fr
            'actions' 1fr / 100%;

        aspect-ratio: 1;
        border: none;
        border-radius: 1rem;
        cursor: pointer;
        width: 100%;
        padding: 0;
        position: relative;
    }

    .selected > .chapter::after {
        content: attr(data-chapter-summary);
        position: absolute;
        top: 0;
        right: -24rem;
        height: 30%;
        border-radius: 1rem;
        padding: 1rem;
        background-color: var(--og-color-white);
    }

    .chapter .title {
        grid-area: title;
        border-radius: 1rem;
        background-color: rgba(0, 0, 0, 0.5);
    }

    .chapter .actions {
        grid-area: actions;
        margin-left: auto;
        margin-right: 1rem;
    }

    .chapter .title, .chapter .actions a {
        font-size: large;
        color: var(--og-color-white);
    }

    .actions a {
        padding: 0.5rem 1rem;
        margin-block: auto;
        background-color: var(--og-color-lgreen);
        border-radius: 1rem;
        text-decoration: none;
    }

    li.selected .chapter {
        width: 100%;
    }

    li.selected + li, li:has(+ li.selected) {
        min-width: 25%;
    }

    .chapter-0 {
        background: url("https://images.unsplash.com/photo-1616892488352-3581f2b56646?q=80&w=1886&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-1 {
        background: url("https://images.unsplash.com/photo-1605003179269-c446bb939f00?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-2 {
        background: url("https://images.unsplash.com/photo-1713149044236-f265cda17928?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-3 {
        background: url("https://images.unsplash.com/photo-1712211587680-d5b40fedf6f6?q=80&w=1994&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-4 {
        background: url("https://images.unsplash.com/photo-1712522810916-acc79fc58e40?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-5 {
        background: url("https://images.unsplash.com/photo-1714163399590-12e5d8c728f2?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-6 {
        background: url("https://images.unsplash.com/photo-1712753188273-02a1aad37955?q=80&w=1935&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-7 {
        background: url("https://images.unsplash.com/photo-1712236961240-5a0ce3aa9e59?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-8 {
        background: url("https://images.unsplash.com/photo-1710747611095-63a55e7a087c?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }
    .chapter-9 {
        background: url("https://plus.unsplash.com/premium_photo-1671278910068-a7a864327507?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D");
        background-size: cover;
    }






</style>