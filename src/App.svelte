<script>
  import { fade } from "svelte/transition";

  let value = "";
  let isRightCode = true;
  let isVisible = true;

  $: if (value === "p@$1to") {
    console.log("good");
    isRightCode = true;
    isVisible = true;
  } else {
    console.log("bad");
    isRightCode = false;
    if (value.length >= 6) {
      isVisible = true;
    } else {
      isVisible = false;
    }
  }
</script>

<h1>
  Привет
  <br />
  Введи сюда код:
</h1>
<input type="text" id="code" bind:value />

{#if isRightCode}
  <div
    transition:fade={{ delay: 500 }}
    class="message"
    style="background: #2ed573;">
    <h2 transition:fade={{ delay: 1000 }}>
      Молодец!
      <br />
      <br />
      Поздравляю
      <br />
      с прохождением квеста!
      <br />
      Ты успешно собрала все части
      <br />
      кода и теперь тебя ждет
      <br />
      <br />
      ГЛАВНЫЙ ПРИЗ
      <br />
      <br />
      Отправь мне скриншот
      <br />
      этого экрана
    </h2>
  </div>
{:else}
  {#if isVisible}
    <div class="message" style="background: #ff4757;">
      <h2 transition:fade>
        Не пытайся угадать :D
        <br />
        <br />
        <br />
        А лучше пройди
        <br />
        квест до конца,
        <br />
        собери все части кода
        <br />
        и сразу введи верный
      </h2>
    </div>
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

  .message {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  h2 {
    color: white;
    text-align: center;
  }
</style>
