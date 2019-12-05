<script>
  import Textarea from "./Textarea.svelte";
  import Header from "./Header.svelte";
  import WordCounter from "./WordCounter.svelte";

  let count;

  const calcWordCount = e => {
    if (e.detail == null) {
      count = 0;
    } else {
      const word_list = e.detail
        .split(" ")
        .filter(word => word.length > 0 && word !== " ");
      count = word_list.length;
    }
  };
</script>

<style>
  .mainContainer {
    display: flex;
    width: 100%;
    height: 90%;
    justify-content: space-evenly;
  }
</style>

<Header />
<WordCounter wordCount={count} />

<div class="mainContainer">
  <Textarea on:updateWordCount={calcWordCount} />
</div>
