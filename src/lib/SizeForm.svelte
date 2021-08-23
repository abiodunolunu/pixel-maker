<script lang="ts">
  import { createEventDispatcher } from "svelte";

  let width: number | null, height: number | null;
  export let maxWidth;

  const emit = createEventDispatcher();

  const handleSubmit = (e: Event) => {
    emit("size", { width: width, height: height });
    width = null;
    height = null;
  };

  export let style = $$props.style;
</script>

<div {style}>
  <form on:submit|preventDefault={handleSubmit}>
    <label>
      <span>Width (max width is {maxWidth})</span>
      <input type="number" bind:value={width} min="1" max={maxWidth} required />
    </label>
    <label>
      <span>Height</span>
      <input type="number" bind:value={height} min="1" required />
    </label>

    <button>Create Art Board</button>
  </form>
</div>

<style>
  form {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
  label {
    display: block;
  }

  label span {
    font-size: 0.875rem;
    color: rgba(0, 0, 0, 0.7);
    display: inline-block;
    margin-bottom: 2px;
  }

  input {
    display: block;
    width: 100%;
    height: 40px;
    border: 1px solid #d5d5d5;
    border-radius: 4px;
    outline: none;
    text-align: center;
  }

  input:focus {
    border: 1px solid rgba(255, 69, 0, 0.5);
  }

  button {
    grid-column: 1 / -1;
    width: 200px;
    margin: 0 auto;
    height: 40px;
    border-radius: 4px;
    border: 0;
    background-color: orangered;
    color: #fff;
    font-weight: 500;
    cursor: pointer;
  }

  button:focus,
  button:hover {
    border: 2px solid orangered;
    background-color: transparent;
    color: orangered;
  }
</style>
