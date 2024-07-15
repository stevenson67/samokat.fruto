<template>
  <section class="rules-promo">
    <div class="container">
      <h2 class="rules-promo__title title"><a href="https://terms.samokat.ru/promo/Pravila_akcii_Novogodnij_advent-kalendar.pdf" target="_blank">Правила акции</a></h2>
      <div class="rules-promo__accordion">
        <div
          class="rules-promo__item"
          v-for="(item, index) in items"
          :key="index"
          @click="toggleActive(index)"
          :class="{ 'active': item.active }"
        >
          <h3 class="rules-promo__subtitle">{{ item.subtitle }}</h3>
          <div class="rules-promo__desc">
            <p v-html="item.description"></p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "rules-promo",
  data() {
    return {
      items: [
        { subtitle: 'Когда и как объявят победителей розыгрыша?', description: 'Мы определим победителей до 29 декабря 2023 года и отправим участникам СМС.', active: false },
        { subtitle: 'Как стать участником розыгрыша?', description: 'Выполните правила, указанные в карточке календаря. А чтобы точно всё получилось, можно посмотреть условия акции <a href="https://terms.samokat.ru/promo/Pravila_akcii_Novogodnij_advent-kalendar.pdf">здесь</a>. <br><br>Быть участниками розыгрыша могут пользователи старше 18 лет.', active: false },
        { subtitle: 'Как я могу применить промокод?', description: 'Скопируйте промокод из карточки календаря и укажите его в корзине в поле «Промокод». <br><br>Вы можете применить промокод только один раз — в дату, указанную на карточке календаря.', active: false },
        { subtitle: 'Как получить приз?', description: 'Мы пришлём СМС с адресом электронной почты. На неё вы отправите свои персональные данные, чтобы мы знали, куда доставить приз.', active: false },
        { subtitle: 'Всё сломалось. Что делать?', description: 'Если вы верно выполнили все условия акции, но промокоды не срабатывают, напишите в поддержку Самоката.', active: false }
      ]
    };
  },
  methods: {
    toggleActive(index) {
      this.items.forEach((item, i) => {
        if (i !== index) {
          item.active = false; // Remove active class from other items
        }
      });
      this.items[index].active = !this.items[index].active; // Toggle active class on the clicked item
    }
  }
};
</script>

<style lang="scss">
.rules-promo {
  padding: 70px 0;
  &__title {
    a {
      text-decoration: underline;
      color: #000000;
    }
  }
  &__accordion {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  &__item {
    border-radius: 18px;
    background: #FFF;
    padding: 16px;
  }
  &__subtitle {
    position: relative;
    cursor: pointer;
    font-size: 18px;
    font-weight: 500;
    line-height: 24px;
    padding-right: 15%;
  }
  &__subtitle::after {
    content: '';
    color: #000000;
    position: absolute;
    top: 15%;
    right: 0;
    width: 24px;
    height: 24px;
    background: url("../static/media/arrow.svg");
    transform: rotate(180deg);
    transition: all 0.3s;
  }
  &__item.active &__subtitle::after {
    transform: rotate(0deg);

  }
  &__desc {
    position: relative;
    height: 0;
    overflow: hidden;
    transition: height 0.3s;
    width: 50%;
      p {
        font-size: 16px;
        font-weight: 400;
        line-height: 24px;
        color: #999;
        padding-top: 12px;
      }
      a {
        color: var(--coral);
      }
  }
  &__item.active &__desc {
    height: auto;
  }
}
@media (max-width: 768px) {
  .rules-promo {
    padding: 36px 0;
    &__desc {
      width: 100%;
    }
  }
}
</style>
