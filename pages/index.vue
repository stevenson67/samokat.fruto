<template>
  <main class="main">
    <cookies/>
    <hero/>
    <rules-list/>
    <calendar/>
    <rules-promo/>
    <footr/>
  </main>
</template>

<script>
import Hero from "~/sections/hero";
import Footr from "@/sections/footr";
import Cookies from "@/components/cookies";
import RulesList from "~/sections/rules-list.vue";
import RulesPromo from "~/sections/rules-promo.vue";
import Calendar from "~/sections/calendar.vue";
export default {
  components: {Calendar, RulesPromo, RulesList, Cookies, Footr, Hero},
  methods: {
    scrollToForm() {
      let calendar = document.querySelector('.calendar')
      window.scroll({
        behavior: 'smooth', left: 0,
        top: calendar.offsetTop
      });
    }
  },
  mounted() {
    document.addEventListener('scroll', function () {
      let offset = window.scrollY - window.innerHeight / 100

      document.querySelectorAll('.scroll-1').forEach(item => {
        item.style = `transform: translate3d(-${offset/20}px, -${offset/20}px, 0)`
      })
      document.querySelectorAll('.scroll-2').forEach(item => {
        item.style = `transform: translate3d(-${offset/10}px, -${offset/20}px, 0)`
      })
      document.querySelectorAll('.scroll-3').forEach(item => {
        item.style = `transform: translateY(-${offset/15}px)`
      })
      document.querySelectorAll('.scroll-4').forEach(item => {
        item.style = `transform: translate3d(${offset/5}px, -${offset/10}px, 0)`
      })
      document.querySelectorAll('.scroll-h').forEach(item => {
        item.style = `transform: translate3d(${offset/10}px, ${offset/20}px, 0)`
      })
      document.querySelectorAll('svg path.scroll-hi').forEach(item => {
        item.style = `transform: rotate(-${offset/20}deg)`
      })

      document.querySelectorAll('svg path.scroll-light').forEach(item => {
        let bound = item.getBoundingClientRect()
        if (bound.top < window.innerHeight/1.75)
          item.classList.add('active')
        else
          item.classList.remove('active')
      })
    })

    document.querySelectorAll('.button.start').forEach(item => {
      item.addEventListener('click', this.scrollToForm)
      item.addEventListener('touchend', this.scrollToForm)
    })
  }
}
</script>
