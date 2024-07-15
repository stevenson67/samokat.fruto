<template>
  <section class="rules-list">
    <img class="rules-list__circle" src="../static/media/circle.svg">
    <div class="container">
      <p class="rules-list__desc">До Нового года осталось совсем немного. Чтобы считать дни до праздника было приятнее, мы решили сделать <span>адвент-календарь</span> с приятными призами</p>
      <h3 class="rules-list__subtitle">Вот как можно стать участником:</h3>
      <div class="rules-list__columns">
        <div class="rules-list__column">
          <span class="rules-list__num"></span>
          <div class="rules-list__text">
            <p>Открывайте новые карточки каждый день</p>
          </div>
        </div>
        <div class="rules-list__column">
          <span class="rules-list__num"></span>
          <div class="rules-list__text">
            <p>Выполняйте несложные задания</p>
          </div>
        </div>
        <div class="rules-list__column">
          <span class="rules-list__num"></span>
          <div class="rules-list__text">
            <p>Получите промокод на скидку или шанс выиграть ценные призы</p>
          </div>
        </div>
      </div>
      <img class="rules-list__star scroll-h" src="../static/media/star-rules-list.svg">
      <img class="rules-list__ellipse_small scroll-1" src="../static/media/ellipse-small.svg">
    </div>
  </section>
</template>

<script>
export default {
  name: "rules-list"
}
</script>

<style lang="scss">
.rules-list {
  position: relative;
  padding: 70px 0;
  &__columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 22px;
  }
  &__column {
    position: relative;
    display: flex;
    align-items: flex-start;
    gap: 14px;
    border-radius: 18px;
    background: var(--white);
    padding: 20px;
    h2 {
      font-size: 22px;
      font-weight: 500;
      line-height: 32px;
    }
    p {
      font-size: 16px;
      font-weight: 400;
      line-height: 24px;
    }
  }
  &__text {
    display: flex;
    flex-direction: column;
    gap: 8px;
    width: 85%;
  }
  &__desc {
    font-size: 18px;
    font-weight: 500;
    line-height: 26px;
    margin-bottom: 32px;
    span {
      color: var(--coral);
    }
  }
  &__subtitle {
    color: var(--coral);
    font-size: 20px;
    font-weight: 500;
    line-height: 32px;
    margin-bottom: 24px;
  }
  &__num {
    width: 15%;
  }
  &__num::before {
    content: '';
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 32px;
    height: 32px;
    border-radius: 20px;
    background: var(--coral);
    font-size: 18px;
    color: var(--white);
  }
  &__column:nth-child(1) span::before {
    content: '1';
  }
  &__column:nth-child(2) span::before {
    content: '2';
  }
  &__column:nth-child(3) span::before {
    content: '3';
  }
  &__circle {
    position: absolute;
    right: 0;
    top: 0;
    display: none;
  }
  &__star {
    position: absolute;
    right: 0;
    top: 120px;
    z-index: -1;
  }
  &__ellipse_small {
    position: absolute;
    left: 55%;
    top: 90%;
    z-index: -1;
  }
}
@media (max-width: 768px) {
  .rules-list {
    padding: 36px 0;
    &__columns {
      grid-template-columns: 1fr;
      gap: 22px;
    }
    &__column {
      gap: 0;
      border-radius: 0;
      background: transparent;
      padding: 0;
    }
    &__text {
      h3 {
        display: none;
      }
    }
    &__num::before {
      width: 24px; height: 24px;
      font-size: 14px;
    }
    &__star {
      right: auto;
      left: -60px;
      width: 25%;
    }
    &__circle {
      display: block;
    }
    &__ellipse_small {
      left: auto;
      right: 0;
      top: 100%;
    }
  }
}
</style>
