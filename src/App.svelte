<script lang="ts">
  import GlobalStyles from "./globalStyles.svelte";
  import Painter from "./lib/Painter.svelte";
  import SizeForm from "./lib/SizeForm.svelte";

  let color = "#ffaa55";
  let height = 10;
  let width = 10;
  let maxWidth;
  let showPainter = true;

  const setSize = (e: any) => {
    width = e.detail.width;
    height = e.detail.height;
  };

  let painterWidth;

  $: {
    maxWidth = Math.round((painterWidth - 40) / 20);
  }
</script>

<main>
  <GlobalStyles />
  <div class="container" bind:clientWidth={painterWidth}>
    <h1>Pixel Art Maker</h1>
    <SizeForm on:size={setSize} {maxWidth} />
    <div style="display: flex; justify-content: center; align-items: center; margin: 1rem 0;">
      <input type="color" bind:value={color} />
    </div>
    {#if showPainter}
      <Painter {height} {width} {color} />
    {/if}
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  h1 {
    text-align: center;
    padding: 1rem 0;
    color: orangered;
  }
</style>
