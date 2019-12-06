<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let filename;

  const passDataUp = contents => {
    dispatch("addContent", contents);
  };

  const passNameUp = name => {
    name = name
      .split("\\")
      .slice(-1)[0]
      .slice(0, -4);
    dispatch("addName", name);
  };

  const handleFile = e => {
    const file = e.target.files[0];
    const reader = new FileReader();
    reader.onloadend = event => {
      if (event.target.readyState == FileReader.DONE) {
        passDataUp(event.target.result);
      }
    };
    reader.readAsText(file);
    passNameUp(filename);
  };
</script>

<style>
  div {
    border: none;
    border-radius: 5px;
    color: white;
    text-align: center;
  }
</style>

<div>
  <input type="file" bind:value={filename} on:change={handleFile} />
</div>
