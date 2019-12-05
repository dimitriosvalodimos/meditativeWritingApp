<script>
  export let wordCount;
</script>

<style>
  div {
    display: inline;
    text-align: center;
  }
  h4 {
    color: white;
  }
</style>

<div>
  <h4>{wordCount ? `${wordCount} words` : '0 words'}</h4>
</div>
