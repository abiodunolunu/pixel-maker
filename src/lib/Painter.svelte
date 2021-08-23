<script lang="ts">
  import { onMount } from "svelte";
  import PixelRow from "./PixelRow.svelte";

  export let height: number;
  export let width: number;
  export let color;

  let canvas: HTMLDivElement;
  let canPaint = false;

  export let style = $$props.style;

  onMount(() => {
    canvas.addEventListener("mousedown", function (e) {
      canPaint = true;
    });

    canvas.addEventListener("mouseup", function (e) {
      canPaint = false;
    });
  });
</script>

<div bind:this={canvas} {style}>
  <p>{width} * {height}</p>
  {#each Array(height) as h, i}
    <PixelRow {width} {canPaint} {color} />
  {/each}
</div>

<style>
  div {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  p {
    margin: 0.2rem 0;
    color: #555;
    font-size: 12px;
    font-style: italic;
  }
</style>
