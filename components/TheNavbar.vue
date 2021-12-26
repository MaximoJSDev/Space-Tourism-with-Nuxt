<template>
  <header class="header">
    <img class="header__logo" src="~/assets/shared/logo.svg" alt="logo" />
    <nav class="nav" :class="{ 'nav--active': isMenuActive }">
      <ul class="nav__menu">
        <li @click="toggleMenu()">
          <NuxtLink to="/">
            <span>00</span> HOME
          </NuxtLink>
        </li>
        <li @click="toggleMenu()">
          <NuxtLink to="/destination">
            <span>01</span> DESTINATION
          </NuxtLink>
        </li>
        <li @click="toggleMenu()">
          <NuxtLink to="/crew">
            <span>02</span> CREW
          </NuxtLink>
        </li>
        <li @click="toggleMenu()">
          <NuxtLink to="/technology">
            <span>03</span> TECHNOLOGY
          </NuxtLink>
        </li>
      </ul>
    </nav>
    <div
      class="ico-menu"
      :class="{ close: isMenuActive }"
      @click="toggleMenu()"
    ></div>
  </header>
</template>
<script>
export default {
  data() {
    return {
      isMenuActive: false,
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuActive = !this.isMenuActive
    },
  },
}
</script>
