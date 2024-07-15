<template>
  <section class="hero">
    <div class="container">
      <a class="hero__logo" href="/">
        <logo/>
      </a>
      <h1 class="hero__title">Новогодние призы от Самоката</h1>
      <div class="hero__subtitle">
        На нашей ёлке много классных подарков: сертификаты на технику и путешествие, а также промокоды на покупки в Самокате
      </div>
      <div class="button start">Получить приз</div>
    </div>
  </section>
</template>

<script>
import Logo from "@/components/logo";
export default {
  name: "hero",
  components: {Logo}
}
</script>

<style lang="scss">
.hero {
  position: relative;
  &__logo {
    display: flex;
    margin: 28px 0 56px 0;
    height: 16px;
  }
  &__title {
    margin: 16px 0;
    color: var(--green);
    text-align: center;
  }
  &__subtitle {
    text-align: center;
  }
  .button { display: none; }
}
</style>
