<script>
  import { onMount } from 'svelte';
  import logo from './assets/icon-dice.svg';
  import dividerMobile from './assets/pattern-divider-mobile.svg';
  import dividerDesktop from './assets/pattern-divider-desktop.svg';
  let innerWidth = 0;
  let adviceText = '';
  let adviceId = 0;

  onMount(async () => {
    const res = await fetch('https://api.adviceslip.com/advice');
    const text = await res.json();
    console.log(`advice: ${text.slip.advice}`);
    adviceText = text.slip.advice;
    adviceId = text.slip.id;
  });

  function handleClick() {
    const res = fetch('https://api.adviceslip.com/advice');
    res
      .then((data) => {
        return data.json();
      })
      .then((text) => {
        adviceId = text.slip.id;
        adviceText = text.slip.advice;
      });
  }
</script>

<svelte:window bind:innerWidth />
<main class="advice-card">
  {#await adviceId}
    <h2 class="title">Loading...</h2>
  {:then adviceId}
    <h2 class="title">Advice #{adviceId}</h2>
  {/await}
  {#await adviceText}
    <h3 class="advice-text">Fetching advice...</h3>
  {:then adviceText}
    <h3 class="advice-text">
      {adviceText}
    </h3>
  {/await}
  {#if innerWidth < 768}
    <img class="divider" src={dividerMobile} alt="divider-mobile" />
  {:else}
    <img class="divider" src={dividerDesktop} alt="divider-mobile" />
  {/if}
</main>

<button on:click={handleClick} class="advice-button"
  ><img src={logo} width="24px" height="24px" alt="logo" /></button
>

<style>
  .advice-card {
    width: 343px;
    height: 315px;
    background-color: #313a48;
    border-radius: 10px;
  }

  .title {
    font-family: 'Manrope', sans-serif;
    color: #53ffaa;
    font-size: 11px;
    line-height: 15px;
    letter-spacing: 3.46px;
    text-align: center;
    margin-top: 40px;
  }

  .advice-text {
    font-family: 'Manrope', sans-serif;
    color: #cee3e9;
    font-weight: 800;
    font-size: 24px;
    line-height: 32.78px;
    letter-spacing: -0.26px;
    text-align: center;
    margin-left: 24px;
    margin-right: 24px;
    margin-top: 0px;
    margin-bottom: 0px;
  }

  .divider {
    margin-top: 24px;
    margin-left: 24px;
    margin-right: 24px;
    height: 15px;
    width: 295px;
  }

  .advice-button {
    display: block;
    width: 64px;
    height: 64px;
    border-radius: 100%;
    margin-top: -32px;
    background-color: #53ffaa;
    border: 1px solid #53ffaa;
  }

  .advice-button:hover {
    box-shadow: 0px 0px 10px #53ffaa;
  }

  .advice-button:active {
    transform: translateY(2px);
  }

  @media screen and (min-width: 768px) {
    .advice-card {
      width: 540px;
      height: 364px;
      background-color: #313a48;
      border-radius: 15px;
    }

    .title {
      font-family: 'Manrope', sans-serif;
      color: #53ffaa;
      font-size: 13px;
      line-height: 17.76px;
      letter-spacing: 4.09px;
      text-align: center;
      margin-top: 48px;
      margin-bottom: 0px;
    }

    .advice-text {
      font-family: 'Manrope', sans-serif;
      width: 444px;
      height: 114px;
      color: #cee3e9;
      font-weight: 800;
      font-size: 28px;
      line-height: 38.25px;
      letter-spacing: -0.3px;
      text-align: center;
      margin-left: 48px;
      margin-right: 48px;
      margin-top: 24px;
      margin-bottom: 0px;
    }

    .divider {
      margin-top: 40px;
      margin-left: 48px;
      margin-right: 48px;
      height: 16px;
      width: 444px;
    }

    .advice-button {
      display: block;
      width: 64px;
      height: 64px;
      border-radius: 100%;
      margin-top: -32px;
      background-color: #53ffaa;
      border: 1px solid #53ffaa;
    }
  }
</style>
