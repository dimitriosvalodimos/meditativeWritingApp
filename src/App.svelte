<script>
  import Textarea from "./Textarea.svelte";
  import Header from "./Header.svelte";
  import WritingGuide from "./WritingGuide.svelte";
</script>

<style>
  .textContainer {
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: space-evenly;
  }
  .guideContainer {
    width: 20%;
    display: flex;
    justify-content: center;
  }
</style>

<Header />
<div class="textContainer">
  <Textarea />
  <div class="guideContainer">
    <WritingGuide />
  </div>
</div>
