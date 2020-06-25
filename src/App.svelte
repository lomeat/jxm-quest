<script>
  let value = "";
  let isRightCode = false;

  $: if (value === "pasito") {
    console.log("good");
    isRightCode = true;
  } else {
    console.log("bad");
    isRightCode = false;
  }
</script>

<h1>
  Привет
  <br />
  Введи сюда код:
</h1>
<input type="text" id="code" bind:value />
{#if isRightCode}
  <h2>Молодец!</h2>
{:else}
  {#if value.length >= 6}
    <h2>Не пытайся угадать :D</h2>
  {/if}
{/if}

<style lang="scss">
  :global(body) {
    margin: 0;
    padding: 0;
    height: 100vh;
    background: #c8d6e5;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  :global(*) {
    margin: 0;
    padding: 0;
    user-select: none;
    outline: none;
  }

  h1 {
    padding-bottom: 100px;
    text-align: center;
  }

  #code {
    padding: 10px;
    border-radius: 8px;
    font-size: 26px;
    font-weight: bold;
    text-transform: uppercase;
    width: 200px;
    text-align: center;
  }
</style>
