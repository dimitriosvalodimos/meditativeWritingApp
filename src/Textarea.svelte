<script>
  import saveAs from "file-saver";

  let text;
  let name;

  const getFilename = () => {
    let filename;
    if (name !== undefined) {
      filename = `${name}.txt`;
    } else {
      const today = new Date();
      const year = today.getFullYear();
      const month = String(today.getMonth() + 1).padStart(2, "0");
      const day = String(today.getDate()).padStart(2, "0");
      filename = `${year}-${month}-${day}`;
    }
    return filename;
  };

  const handleDataDownload = e => {
    e.preventDefault();
    const blob = new Blob([text], { type: "text/plain;charset=utf-8" });
    const filename = getFilename();
    saveAs(blob, filename);
  };
</script>

<style>
  form {
    width: 60%;
  }
  textarea {
    display: block;
    border: none;
    border-radius: 5px;
    overflow: auto;
    outline: none;
    box-shadow: none;
    resize: none;
    width: 100%;
    height: 60%;
    margin-bottom: 1rem;
  }

  div {
    text-align: center;
    margin: 1rem;
  }

  input {
    border-radius: 5px;
  }

  button {
    border-radius: 5px;
  }
</style>

<form action="">
  <textarea
    placeholder="Start your writing here..."
    cols="30"
    rows="10"
    bind:value={text} />
  <div>
    <input type="text" placeholder="Enter filename" bind:value={name} />
    <button type="submit" on:click={handleDataDownload}>Save</button>
  </div>
</form>
