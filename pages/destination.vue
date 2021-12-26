<template>
  <main class="destination">
    <h2 class="title-section"><span>01</span> Pick your destination</h2>
    <div
      class="grid-center mt"
      v-if="destinations !== undefined && destinations.length !== 0"
    >
      <div class="trick-container"></div>
      <div class="destination__menu-astro" @click="changeSection">
        <span class="destination__container__names" id="moon">MOON</span>
        <span class="destination__container__names" id="mars">MARS</span>
        <span class="destination__container__names" id="europa">EUROPA</span>
        <span class="destination__container__names" id="titan">TITAN</span>
      </div>
      <div class="destination__content-img">
        <img
          class="destination__content-img__img"
          :src="require(`~/${destinations[i].images.png}`)"
          :alt="destinations[i].name"
        />
      </div>
      <article class="card">
        <h1 class="card__title">{{ destinations[i].name }}</h1>
        <p class="card__info">
          {{ destinations[i].description }}
        </p>

        <div class="card__distance">
          <div class="card__distance__container">
            <h3 class="card__distance__title">AVG. DISTANCE</h3>
            <p class="card__distance__info">{{ destinations[i].distance }}</p>
          </div>
          <div class="card__distance__container">
            <h3 class="card__distance__title">Est. travel time</h3>
            <p class="card__distance__info">{{ destinations[i].travel }}</p>
          </div>
        </div>
      </article>
    </div>
  </main>
</template>

<script>
export default {
  head() {
    return {
      title: 'Space Tourism - Destination',
    }
  },
  data() {
    return {
      destinations: [],
      i: 0,
    }
  },
  methods: {
    changeSection(evnt) {
      const { target } = evnt
      if (target.classList.contains('destination__container__names')) {
        if (target.id == 'moon') this.i = 0
        if (target.id == 'mars') this.i = 1
        if (target.id == 'europa') this.i = 2
        if (target.id == 'titan') this.i = 3
      }
    },
  },
  created() {
    fetch('data.json')
      .then((res) => res.json())
      .then((data) => {
        this.destinations = data.destinations
        console.log(data.destinations)
      })
  },
}
</script>

<style>
.destination {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background: #0b0d17
    url('~assets/destination/background-destination-desktop.jpg');
  background-size: cover;
  background-blend-mode: luminosity;
  color: #fff;
  overflow-x: hidden;
}
.destination__menu-astro {
  width: 445px;
  height: 34px;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  column-gap: 36px;
}
.destination__container__names {
  font-family: 'Barlow Condensed', sans-serif;
  font-size: 16px;
  line-height: 19px;
  letter-spacing: 2.7px;
  color: #d0d6f9;
  cursor: pointer;
}
@media (max-width: 1220px) {
  .grid-center {
    grid-template-columns: 1fr;
  }
  .mt {
    margin-top: 16rem;
  }
  .trick-container {
    display: none;
  }
  .destination__menu-astro {
    margin-top: 52px;
    justify-content: center;
    grid-row: 2/3;
  }
  .destination .card {
    width: 82vw;
    max-width: 573px;
    height: 430px;
    justify-content: flex-start;
    align-items: center;
    text-align: center;
  }
  .destination .card__title {
    font-size: 80px;
    margin-bottom: 8px;
  }
  .destination .card__info {
    margin-bottom: 49px;
  }
  .destination .card__distance {
    justify-content: center;
  }
  .destination .card__distance__container {
    align-items: center;
  }
  .destination__content-img__img {
    width: 300px;
  }
}
@media (max-width: 560px) {
  .destination__content-img__img {
    width: 150px;
  }
  .destination__container__names {
    font-size: 14px;
  }
  .destination .card {
    height: auto;
  }
  .destination .card__title {
    font-size: 58px;
    line-height: normal;
    margin-top: 20px;
  }
  .destination .card__distance {
    flex-direction: column;
    row-gap: 32px;
  }
}
</style>
