<template>
  <section class="calendar">
    <div class="container">
      <h2 class="calendar__title title">Календарь</h2>
      <div class="calendar__wrap">
        <div class="calendar__num" >
          <span v-for="day in days" :key="day" :class="{ 'not-active': day < currentDay, 'active': day === currentDay }">{{ day }}</span>
          <img class="calendar__star scroll-2" src="../static/media/star-hero.svg">
          <img class="calendar__ellipse_small scroll-3" src="../static/media/ellipse-small.svg">
          <img class="calendar__ellipse_large scroll-3" src="../static/media/ellipse-large.svg">
        </div>
        <div class="calendar__info">
          <img class="calendar__star_yellow" src="../static/media/calendar-star-yellow.svg">
          <img class="calendar__star_white" src="../static/media/calendar-star-white.svg">
          <img class="calendar__circle" src="../static/media/calendar-circle.svg">
          <span class="calendar__date">{{ currentDate }} декабря</span>
          <div class="calendar__main">
            <img class="calendar__img" :src="currentImage" :alt="'Calendar for day ' + currentDay">
            <a class="calendar__btn" @click="showPopup">Нажмите чтобы активировать</a>
          </div>
        </div>
      </div>
      <popup v-if="isPopupVisible" @close="isPopupVisible = false" :img-index="currentDate" :title="getCurrentDesc().title" :code="getCurrentDesc().code" :link="getCurrentDesc().link">
        <span>{{ getCurrentDesc().descSpan }}</span>
        <p>{{ getCurrentDesc().desc }}</p>
      </popup>
    </div>
  </section>
</template>

<script>

import Popup from "~/sections/popup.vue";

export default {
  name: "calendar",
  components: {Popup},
  data: () => ({
    days: Array.from({ length: 21 }, (_, i) => i + 1),
    imagesPath: '/media/calendar/calendar-',
    currentDay: 1,
    isPopupVisible: false,
    popup: [
      {
        id: 1,
        title: 'Мешок с подарками',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш мешка подарков с товарами ФрутоНяня',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
      {
        id: 2,
        title: 'Промокод',
        code: 'МОЛОКО40',
        desc: 'Дарим скидку 40% на три любых молочных продукта ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/77674095-f7c4-4cbd-94b3-b36288743952?showcaseType=MINIMARKET',
      },
      {
        id: 3,
        title: 'Умная колонка',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш умной колонки',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
      {
        id: 4,
        title: 'Промокод',
        code: 'ПЮРЕ50',
        desc: 'Дарим скидку 50% на пять пюре ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/01833609-2c72-4458-a83c-8f63d04d9eca?showcaseType=MINIMARKET',
      },
      {
        id: 5,
        title: 'Промокод',
        code: 'КАШКА35',
        desc: 'Дарим скидку 35% на две сухие кашки ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/a7705d81-779c-4cc7-af21-92da642c2eb5?showcaseType=MINIMARKET',
      },
      {
        id: 6,
        title: 'Промокод',
        code: 'СОК40',
        desc: 'Дарим скидку 40% на пять соков ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/5dc4fc18-a3af-47f6-803b-b22969b13248?showcaseType=MINIMARKET',
      },
      {
        id: 7,
        title: 'Промокод',
        code: 'СНЕКИ25',
        desc: 'Дарим скидку 25% на любые три снека ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/28ac0a86-7943-4c17-ad22-d02c42125865?showcaseType=MINIMARKET',
      },
      {
        id: 8,
        title: 'Промокод',
        code: 'КАШКА40',
        desc: 'Дарим скидку 40% на три жидкие кашки ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/47052070-e0fb-4940-aed4-331418b7fbcd?showcaseType=MINIMARKET',
      },
      {
        id: 9,
        title: 'Мешок с подарками',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш мешка подарков с товарами ФрутоНяня',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
      {
        id: 10,
        title: 'Промокод',
        code: 'ПЮРЕ30',
        desc: 'Дарим скидку 30% на три мясных пюре ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/fae99862-4754-43db-8bc5-6688e6802a5b?showcaseType=MINIMARKET',
      },
      {
        id: 11,
        title: 'Промокод',
        code: 'МОЛОКО50',
        desc: 'Дарим скидку 50% на пять любых молочных продуктов ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/35b4d571-249c-4dfa-b154-ec7f5fd0e885?showcaseType=MINIMARKET',
      },
      {
        id: 12,
        title: 'Промокод',
        code: 'ПЮРЕ_30',
        desc: 'Дарим скидку 30% на три овощных пюре ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/1add1aac-00ba-4090-b1a5-e6a660ec700d?showcaseType=MINIMARKET',
      },
      {
        id: 13,
        title: 'Толстовка',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш толстовки ФрутоНяня',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
      {
        id: 14,
        title: 'Промокод',
        code: 'ПЮРЕ_40',
        desc: 'Дарим скидку 40% на пять пюре в стеклянной упаковке ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/5b2fa33d-adf6-4ff1-98ba-6a7763995e53?showcaseType=MINIMARKET',
      },
      {
        id: 15,
        title: 'Промокод',
        code: 'КАШКА_40',
        desc: 'Дарим скидку 40% на три жидкие кашки ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/c9241ff3-c940-4a36-9202-60df4f41632c?showcaseType=MINIMARKET',
      },
      {
        id: 16,
        title: 'Промокод',
        code: 'ПЮРЕ40',
        desc: 'Дарим скидку 40% на три любых пюре ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/112d1723-d5e3-45d2-8482-5fe40cfb2b20?showcaseType=MINIMARKET',
      },
      {
        id: 17,
        title: 'Промокод',
        code: 'СНЕКИ30',
        desc: 'Дарим скидку 30% на любые три снека ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/b191fdf5-a961-4b7b-82a7-07573a4a34bd?showcaseType=MINIMARKET',
      },
      {
        id: 18,
        title: 'Промо за 1 рубль',
        desc: 'Выберите два любых пюре из подборки и получите фруктовый мармелад Осьминожка за 1 ₽',
        descSpan: 'Дарим фруктовую осьминожку за 1 ₽',
        link: 'https://samokat.go.link/promocategory/d7a9e743-22a6-4c90-b264-ae1d434e4ade?showcaseType=MINIMARKET',
      },
      {
        id: 19,
        title: 'Промокод',
        code: 'СОК_40',
        desc: 'Дарим скидку 40% на пять любых соков ФрутоНяня',
        descSpan: '',
        link: 'https://samokat.go.link/promocategory/fa198952-5e17-497a-95b2-af5707dbbd5d?showcaseType=MINIMARKET',
      },
      {
        id: 20,
        title: 'Набор детских игрушек',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш детских игрушек',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
      {
        id: 21,
        title: 'Набор детских игрушек',
        desc: 'Чтобы поучаствовать, добавьте в корзину продукты ФрутоНяня на 100 ₽ и оформите заказ',
        descSpan: 'Розыгрыш детских игрушек',
        link: 'https://samokat.go.link/promocategory/54a090eb-70b1-4a89-94e5-5c61d2f7a0da?showcaseType=MINIMARKET',
      },
    ]
  }),
  methods: {
    async changeColor() {
      const response = await fetch('https://worldtimeapi.org/api/timezone/Europe/Moscow');
      const data = await response.json();
      const currentDate = new Date(data.datetime).getDate();
      this.currentDay = currentDate;
    },
    showPopup() {
      this.isPopupVisible = true;
    },
    getCurrentDesc() {
      const descObj = this.popup.find(item => item.id === this.currentDate);
      return descObj ? descObj : { desc: '', descSpan: '', code: '', link: '' };
    }
  },
  mounted() {
    this.changeColor();
    setInterval(this.changeColor, 60000);
  },
  computed: {
    currentDate() {
      const currentDate = new Date().getDate();
      return currentDate;
    },
    currentImage() {
      return this.imagesPath + this.currentDay + '.png';
    },
  }
}
</script>

<style lang="scss">
.calendar {
  padding: 70px 0;
  &__wrap {
    display: flex;
    gap: 16px;
  }
  &__num, &__info {
    width: 50%;
  }
  &__num {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    gap: 5px;
    span {
      font-size: 22px;
      font-weight: 500;
      line-height: normal;
      border-radius: 32px 32px 12px 12px;
      background: var(--white);
      text-align: center;
      padding: 19px 10px;
    }
    span.not-active {
      opacity: 0.5;
    }
    span.active {
      border: 1px solid var(--coral);
      color: var(--coral);
      cursor: pointer;
    }
    .calendar__star {
      position: absolute;
      right: 5%;
      bottom: 10%;
      z-index: -1;
    }
    .calendar__ellipse_small {
      position: absolute;
      left: 25%;
      bottom: 3%;
      z-index: -1;
    }
    .calendar__ellipse_large {
      position: absolute;
      right: 0;
      bottom: -3%;
      z-index: -1;
    }
  }
  &__info {
    position: relative;
    display: flex;
    flex-direction: column;
    border-radius: 18px;
    background: var(--coral);
    color: var(--white);
    padding: 20px;
  }
  &__main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
  &__img {
    width: 100%;
  }
  &__btn {
    border-radius: 60px;
    background: #FFF;
    color: var(--coral);
    width: 100%;
    text-align: center;
    padding: 20px;
    cursor: pointer;
  }
  &__star {
    &_yellow {
      position: absolute;
      left: 0;
      top: 25%;
    }
    &_white {
      position: absolute;
      right: 0;
      top: 60%;
    }
  }
  &__circle {
    position: absolute;
    right: 0;
    top: 0;
  }
}

@media (max-width: 768px) {
  .calendar {
    padding: 36px 0;
    &__title {
      margin-bottom: 36px;
    }
    &__wrap {
      flex-direction: column;
    }
    &__num, &__info {
      width: 100%;
    }
    &__info {
      order: -1;
    }
  }
}
</style>
