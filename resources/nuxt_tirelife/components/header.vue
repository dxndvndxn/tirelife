<template>
  <header>
    <div class="header container">
      <div class="header__logo-wrap">
        <nuxt-link to="/">
          <img class="header__logo" src="~/assets/imgs/logo.svg" alt="Tire Life">
        </nuxt-link>
      </div>
      <ul class="header__menu">
        <li v-for="(link, i) in menu">
          <nuxt-link class="header__link" :to="link.link" exact-active-class="active-link">
            {{ link.name }}
          </nuxt-link>
        </li>
      </ul>
      <div class="header__icons">
        <div class="header__cart">
          <img src="~/assets/imgs/cart-icon.svg" alt="Корзина">
        </div>
      </div>
    </div>
  </header>
</template>
<script>
export default {
  data: () => ({
    menu: [
      {
        name: 'магазин',
        link: '/'
      },
      {
        name: 'шиномонтаж',
        link: '/tire-fitting',
      },
      {
        name: 'хранение',
        link: '/storage',
      },
      {
        name: 'контакты',
        link: '/contacts'
      }
    ]
  })
}
</script>
