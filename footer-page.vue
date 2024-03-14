<template>
  <div>
    <div class="followUs">
      <h1>{{ $t("prefooter1") }}</h1>
      <p align="center">
        {{ $t("prefooter2") }}
      </p>
      <form class="back">
        <div class="disable thx" id="thx">
          <h3>Thank for subscribing</h3>
        </div>
        <input class="gg" name="mail" type="email" placeholder="Your e-mail" />
        <button class="gg" type="button" form="back" id="fb">
          {{ $t("prefooter3") }}
        </button>
      </form>
    </div>
    <footer>
      <p>
        {{ $t("footer1") }} <a href="https://patio-style.ru/">patio-style.ru</a>
      </p>
      <p>{{ $t("footer2") }}</p>
      <div class="links">
        <a href=""> <img src="../assets/images/facebook.png" /></a>
        <a href=""> <img src="../assets/images/twitter.png" /></a>
        <a href=""> <img src="../assets/images/inst.png" /></a>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "footer-page",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
