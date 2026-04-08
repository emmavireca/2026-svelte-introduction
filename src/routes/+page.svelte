<script>
    let count = $state(0)

    console.log ("Hello world")
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<!-- svelte-ignore a11y_consider_explicit_label -->
<button onclick={() => count++}>
   Clicks: {count}
</button>

<style>
    h1 {
        color: blue
    }
</style>