<script lang="ts">
  let me: HTMLDivElement;

  export let canPaint: boolean;
  export let color;

  const paintPixel = () => {
    console.log("yeah");
    if (!canPaint) return;

    me.style.backgroundColor = color;
  };

  const paintIndividualPixel = () => {
    me.style.backgroundColor = color;
  };
</script>

<div bind:this={me} on:mouseenter={paintPixel} on:click={paintIndividualPixel} />

<style>
  div {
    height: 20px;
    width: 20px;
    border: 1px solid currentColor;
    flex-shrink: 0;
  }
</style>
