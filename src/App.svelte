<script>
  import logo from './assets/icon-dice.svg';
  import dividerMobile from './assets/pattern-divider-mobile.svg';
</script>

<main class="advice-card">
  <p class="title">Advice #117</p>
  <h1 class="advice-text">
    “It is easy to sit up and take notice, what's difficult is getting up and
    taking action.”
  </h1>
  <img class="divider" src={dividerMobile} alt="divider-mobile" />
</main>

<button class="advice-button"
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
</style>
