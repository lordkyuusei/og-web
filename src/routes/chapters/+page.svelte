<script lang="ts">
    import ChapterSleeve from "$lib/components/ChapterSleeve.svelte";
    import type { ChapterMedatada } from "$lib/types/chapter";

    let chapters: ChapterMedatada[] = [
        { id: 9, title: "TITRE DU CHAPITRE 9", image: "https://images.unsplash.com/photo-1616892488352-3581f2b56646?q=80&w=1886&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 8, title: "TITRE DU CHAPITRE 8", image: "https://images.unsplash.com/photo-1605003179269-c446bb939f00?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 7, title: "TITRE DU CHAPITRE 7", image: "https://images.unsplash.com/photo-1713149044236-f265cda17928?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 6, title: "TITRE DU CHAPITRE 6", image: "https://images.unsplash.com/photo-1712211587680-d5b40fedf6f6?q=80&w=1994&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 5, title: "TITRE DU CHAPITRE 5", image: "https://images.unsplash.com/photo-1712522810916-acc79fc58e40?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 4, title: "TITRE DU CHAPITRE 4", image: "https://images.unsplash.com/photo-1714163399590-12e5d8c728f2?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 3, title: "TITRE DU CHAPITRE 3", image: "https://images.unsplash.com/photo-1712753188273-02a1aad37955?q=80&w=1935&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 2, title: "TITRE DU CHAPITRE 2", image: "https://images.unsplash.com/photo-1712236961240-5a0ce3aa9e59?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 1, title: "TITRE DU CHAPITRE 1", image: "https://images.unsplash.com/photo-1710747611095-63a55e7a087c?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
        { id: 0, title: "TITRE DU CHAPITRE 0", image: "https://plus.unsplash.com/premium_photo-1671278910068-a7a864327507?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D", summary: "RESUME DU CHAPITRE MAIS EN MODE SUPER LONG", date: new Date() },
    ];

    let chaptersRef: HTMLUListElement | null = null;

    let selectedChapter: number | null = chapters[0].id;

    const selectChapter = (event: CustomEvent<{ chapter: ChapterMedatada, target: HTMLButtonElement }>) => {
        const { chapter, target } = event.detail;
        selectedChapter = chapter.id;

        const { left } = target.getBoundingClientRect();
        console.log(left);
        chaptersRef?.scrollBy({ left, behavior: "smooth" });        

        const body = document.querySelector("body");
        if (!body) return;
        
        body.style.background = `url(${chapter.image})`;
    }
</script>

<ul bind:this={chaptersRef}>
    {#each chapters as chapter}
    <li class:selected={chapter.id === selectedChapter}>
        <ChapterSleeve {chapter} isSelected={chapter.id === selectedChapter} on:select={selectChapter}></ChapterSleeve>
    </li>
    {/each}
</ul>

<style>
    :root {
        --selected-width: 33%;
        --previous-width: calc(var(--selected-width) * 75/100);
        --next-width: calc(var(--selected-width) * 60/100);
        --default-width: calc(var(--selected-width) * 50/100);
    }

    ul {
        display: flex;
        align-items: end;
        gap: var(--larger-spacing);
        width: 100%;
        overflow-x: auto;

        scroll-snap-type: inline mandatory;
        scroll-padding-inline: var(--larger-spacing);
    }

    li {
        min-width: var(--default-width);
        transition: all 0.2s cubic-bezier(0.075, 0.82, 0.165, 1);
        scroll-snap-align: start;
    }
        
    li.selected {
        min-width: var(--selected-width);
    }

    /* The one before the selected one */
    li:has(+ li.selected) {
        min-width: var(--previous-width);
    }

    /* The one after the selected one */
    li.selected + li {
        min-width: var(--next-width);
    }
</style>