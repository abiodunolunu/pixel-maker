<script lang="ts">
  import Pixel from "./Pixel.svelte";

  export let width: number;

  export let canPaint;

  export let color;
</script>

<div>
  {#each Array(width) as w, i}
    <Pixel {canPaint} {color} />
  {/each}
</div>

<style>
  div {
    display: flex;
  }

  div {
  }

  div > :global(div) {
    border-bottom: 0;
    border-right: 0;
  }

  div > :global(div):last-of-type {
    border-right: 1px solid currentColor;
  }

  div:last-of-type > :global(div) {
    border-bottom: 1px solid currentColor;
  }
</style>
