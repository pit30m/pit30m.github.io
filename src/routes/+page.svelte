<script>
    import YouTubeVideo from '../YouTubeVideo.svelte';
    let datasetName = "Pit30M"
</script>

<main class="bg-gray-200 min-h-screen flex items-center justify-center">
<div class="text-center">
    <h1 class="text-5xl font-bold mb-6">Welcome to {datasetName}</h1>
    <p class="text-xl mb-8">Thanks for visiting!</p>
    <a href="#" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Get started</a>
    <YouTubeVideo videoId="hJ6A_1YSITo" />
</div>



</main>

<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>