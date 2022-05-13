<template>
  <header class="header">
    <img class="header__logo" src="~/assets/shared/logo.svg" alt="logo" />
    <nav class="nav" :class="{ 'nav--active': isMenuActive }">
      <ul class="nav__menu">
        <li @click="moveIndicator($event), toggleMenu()">
          <NuxtLink to="/">
            <span class="sectionID">00</span> HOME
          </NuxtLink>
        </li>
        <li @click="moveIndicator($event), toggleMenu()">
          <NuxtLink to="/destination">
            <span class="sectionID">01</span> DESTINATION
          </NuxtLink>
        </li>
        <li @click="moveIndicator($event), toggleMenu()">
          <NuxtLink to="/crew">
            <span class="sectionID">02</span> CREW
          </NuxtLink>
        </li>
        <li @click="moveIndicator($event), toggleMenu()">
          <NuxtLink to="/technology">
            <span class="sectionID">03</span> TECHNOLOGY
          </NuxtLink>
        </li>
        <div class="header__menu__marker" ref="marker"></div>
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
    moveIndicator(e) {
      let linkTarget = e.target
      const marker = this.$refs.marker;
      if (e.target.classList.contains("sectionID")) linkTarget = linkTarget.parentElement
      marker.style.left = linkTarget.offsetLeft+'px';
      marker.style.width = linkTarget.offsetWidth+'px';
    }
  },
}
</script>
