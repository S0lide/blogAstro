<script lang="ts">
    import ArticlePreview from "./ArticlePreview.svelte"
    import Database from "../../database.json"
    import { SearchValue } from "../stores/ArticleStore.svelte.ts";

    // Source complète
    const articles = Database.articles

    const filtered = $derived.by(() => {
        const request= $SearchValue.trim().toLowerCase()
        if (!request) return articles
        return articles.filter(article => {
            const title = (article.title ?? '').toLowerCase()
            const author = (article.autor ?? '').toLowerCase()
            return title.includes(request) || author.includes(request)
        })
    })
</script>

<ul>
    {#each filtered as article}
        <ArticlePreview autor={article.autor} tags={article.tags} title={article.title} />
    {/each}
</ul>