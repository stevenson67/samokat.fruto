<template>
  <section class="hero">
    <div class="container">
      <a class="hero__logo" href="/">
        <logo/>
      </a>
      <div class="hero__wrap">
        <div class="hero__text">
          <h1 class="hero__title">Праздничный календарь</h1>
          <div class="hero__subtitle">
            Открывайте новые карточки каждый день, выполняйте задания и выигрывайте классные призы
          </div>
          <a class="button start">Открыть подарок</a>
          <img class="hero__star scroll-4" src="../static/media/star-hero.svg">
        </div>
        <div class="hero__elka">
          <elka-hero/>
        </div>
      </div>
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
  padding: 60px 0 74px 0;
  .container {
    position: relative;
  }
  .container, &__text, &__elka {
    height: 100%;
  }
  &__logo {
    position: absolute;
    display: flex;
    height: 16px;
  }
  &__wrap, &__elka {
    display: flex;
    align-items: flex-end;
    height: 100%;
  }
  &__text {
    width: 40%;
  }
  &__elka {
    width: 60%;
    svg {
      height: 100%;
    }
  }
  &__text {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }
  &__title {
    font-size: 40px;
    font-weight: 500;
    line-height: normal;
    margin: 0 0 20px 0;
  }
  &__subtitle {
    font-size: 16px;
    font-weight: 500;
    line-height: 24px;
    margin-bottom: 44px;
    color: #999;
  }
  &__star {
    position: absolute;
    left: -100px;
    top: 30%;
    z-index: -1;
  }
}
@media (max-width: 768px) {
  .hero {
    padding: 36px 0;
    &__text, &__elka {
      height: auto;
    }
    &__star {
      left: auto;
      right: -50px;
      top: 0;
      width: 25%;
    }
    &__title {
      font-size: 28px;
      line-height: 32px;
    }
    &__subtitle {
      font-size: 16px;
      line-height: 24px;
      margin-bottom: 36px;
    }
    &__wrap {
      justify-content: center;
      flex-direction: column;
      gap: 24px;
    }
    &__text, &__elka {
      width: 100%;
    }
    &__elka {
      justify-content: center;
      order: -1;
      padding-top: 45px;
      svg {
        width: 85%;
      }
    }
  }
}
</style>
