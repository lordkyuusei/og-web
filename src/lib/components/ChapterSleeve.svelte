<script lang="ts">
    import { createEventDispatcher } from "svelte";
    import type { ChapterMedatada } from "$lib/types/chapter";

    export let chapter: ChapterMedatada;
    export let isSelected: boolean;

    const dispatch = createEventDispatcher();

    const selectChapter = (event: Event, chapter: any) => {
        isSelected = true;
        dispatch("select", { chapter, target: event.currentTarget });
    };
</script>

<button
    on:click={(event) => selectChapter(event, chapter)}
    style:background-image="url({chapter.image})"
    class="chapter chapter-{chapter.id} {isSelected ? 'selected': ''}"
    data-chapter-summary={chapter.summary}
>
    <header class="title"><span>{chapter.title}</span></header>
    {#if isSelected}
        <footer class="actions">
            <a href="/comic/{chapter.id}">Read chapter {chapter.id}</a>
        </footer>
    {/if}
</button>

<style>
    .chapter {
        display: grid;
        grid-template:
            "title" 1fr
            "." 9fr
            "actions" 1fr / 100%;

        aspect-ratio: 1;
        border: none;
        border-radius: var(--normal-radius);
        cursor: pointer;
        width: 100%;
        padding: 0;
        position: relative;
        background-size: 100%;
        transition: all 0.25s cubic-bezier(0.075, 0.82, 0.165, 1);
    }

    .chapter:hover {
        transition: all 0.25s cubic-bezier(0.075, 0.82, 0.165, 1);
        background-size: 150%;
    }

    .chapter .title {
        grid-area: title;
        display: grid;
        place-items: center;
        border-radius: var(--normal-radius) var(--normal-radius) 0 0;
        background-color: rgba(0, 0, 0, 0.5);
        height: 100%;
    }

    .chapter .actions {
        grid-area: actions;
        margin-left: auto;
        margin-right: var(--normal-spacing);
    }

    .chapter .title span, .chapter .actions a {
        color: var(--og-color-white);
    }

    .actions a {
        padding: var(--smaller-spacing) var(--normal-spacing);
        margin-block: auto;
        background-color: var(--og-color-lgreen);
        border-radius: var(--normal-radius);
    }

    .selected.chapter::after {
        content: attr(data-chapter-summary);
        position: absolute;
        top: 0;
        right: -24rem;
        height: 30%;
        border-radius: var(--normal-radius);
        padding: var(--normal-spacing);
        background-color: var(--og-color-white);
    }
</style>
