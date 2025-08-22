<script lang="ts">
    import ArticlePreview from "./ArticlePreview.svelte"
    import Database from "../../database.json"
</script>

<ul>
    {#each Database.articles as article}
        <ArticlePreview autor={article.autor} tags={article.tags} title={article.title} />
    {/each}
</ul>