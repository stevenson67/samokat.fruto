<template>
  <aside class="popup">
    <div class="popup__bg" @click="$emit('close')"></div>
    <div class="popup-container">
      <div class="popup__wrap">
        <div class="popup__close" @click="$emit('close')">
          <img src="../static/media/close.svg">
        </div>
        <div class="popup__content">
          <h2 class="popup__title">{{ title }}</h2>
          <img class="popup__img" :src="`../media/popup/popup-${imgIndex}.png`">
          <a class="popup__code" v-if="code" @click="copyCode" v-else >
            {{ copied ? 'Скопировано' : code }}<img src="../static/media/fi_copy.svg">
          </a>
          <p class="popup__desc">
            <slot></slot>
          </p>
        </div>
        <a class="popup__app" v-if="link" :href="link" target="_blank">Заказать в приложении</a>
      </div>
    </div>
  </aside>
</template>

<script>
export default {
  name: "popup",
  props: {
    imgIndex: {
      default: 1
    },
    code: null,
    link: null,
    title: String,
  },
  data() {
    return {
      copied: false
    };
  },
  methods: {
    copyCode() {
      const el = document.createElement('textarea');
      el.value = this.code;
      document.body.appendChild(el);
      el.select();
      document.execCommand('copy');
      document.body.removeChild(el);
      this.copied = true;
      setTimeout(() => {
        this.copied = false;
      }, 2000);
    }
  }
}
</script>

<style lang="scss">
.popup {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  top: 0; left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
  &__bg {
    width: 100%;
    height: 100%;
    z-index: 0;
  }
  &-container {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    max-height: 700px;
    max-width: 400px;
    overflow: hidden;
    background: var(--white);
    border-radius: 20px;
    padding: 24px 20px;
  }
  &__wrap {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
  }
  &__content {
    display: flex;
    flex-direction: column;
    margin-bottom: 44px;
  }
  &__close {
    position: absolute;
    right: 20px;
    top: 20px;
    cursor: pointer;
  }
  &__title {
    font-size: 22px;
    font-style: normal;
    font-weight: 500;
    line-height: 32px;
    color: var(--dark);
  }
  &__code {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    color: var(--coral);
    letter-spacing: 0.16px;
    text-align: center;
    padding: 20px;
    border-radius: 60px;
    border: 1px solid var(--coral);
    margin-bottom: 14px;
    cursor: pointer;
      img {
        position: relative;
        width: 24px;
      }
  }
  &__img {
    width: 100%;
    height: 250px;
    object-fit: contain;
  }
  &__desc {
    font-weight: 400;
    span {
      color: var(--coral);
    }
    p {
      margin-top: 12px;
    }
  }
  &__app {
    padding: 20px 40px;
    background: var(--coral);
    color: var(--white);
    text-align: center;
    cursor: pointer;
    margin: 0 -20px -24px -20px;
  }
}
</style>
