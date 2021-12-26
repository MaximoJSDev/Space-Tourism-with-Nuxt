<template>
  <main id="technology">
    <h2 class="title-section"><span>03</span> SPACE LAUNCH 101</h2>
    <div
      class="flex-center mt"
      v-if="technology !== undefined && technology.length !== 0"
    >
      <div class="num-group" ref="root">
        <span :class="pointActive == 0? 'point-active' : ''" @click="changeLaunch(0)">1</span>
        <span :class="pointActive == 1? 'point-active' : ''" @click="changeLaunch(1)">2</span>
        <span :class="pointActive == 2? 'point-active' : ''" @click="changeLaunch(2)">3</span>
      </div>
      <article class="card">
        <h1 class="card__job">THE TERMINOLOGY…</h1>
        <h3 class="card__title md-title">{{ technology[i].name }}</h3>
        <p class="card__info">
          {{ technology[i].description }}
        </p>
      </article>
      <div class="card__img-container">
        <picture>
          <source
            :srcset="require(`~/${technology[i].images.landscape}`)"
            media="(max-width: 1220px)"
          />
          <img
            class="person"
            :src="require(`~/${technology[i].images.portrait}`)"
            :alt="technology[i].name"
          />
        </picture>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      technology: [],
      i: 0,
      pointActive: 0
    }
  },
  methods: {
    changeLaunch(index) {
      this.i = index
      this.pointActive = index
      // let points = this.$refs.root.childNodes
      // console.log(points)
      // points.forEach((activos) => {
      //   if (activos.nodeName !== '#text') {
      //     console.log(activos)
      //     activos.classList.remove('point-active')
      //   }
      // })
      // if (points[index] !== '#text') points[index].classList.add('point-active')
    },
  },
  created() {
    fetch('data.json')
      .then((res) => res.json())
      .then((data) => (this.technology = data.technology))
  },
}
</script>

<style>
#technology {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background: #0b0d17
    url('~assets/technology/background-technology-desktop.jpg') no-repeat;
  background-size: cover;
  background-blend-mode: luminosity;
  color: #fff;
  overflow: hidden;
}
#technology .flex-center {
  column-gap: 1rem;
}
#technology .card {
  width: 470px;
}
#technology .card__job {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: normal;
  font-size: 16px;
  color: #d0d6f9;
  text-transform: uppercase;
  letter-spacing: 2.7px;
  margin-bottom: 11px;
}
#technology .card__info {
  margin-bottom: 0;
}
.num-group {
  height: 303px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
}
.num-group span {
  font-family: 'Bellefair', serif;
  font-size: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
  border-radius: 50%;
  color: rgb(255, 255, 255);
  border: 1px solid rgba(255, 255, 255, 0.25);
  cursor: pointer;
}
.point-active.point-active {
  background-color: #fff;
  color: #000;
  border-color: transparent;
}
#technology .card__img-container img {
  width: 515px;
  height: 527px;
}
@media (max-width: 1220px) {
  #technology .mt {
    margin-top: 15.85rem;
  }
  #technology .flex-center {
    flex-direction: column-reverse;
    row-gap: 50px;
  }
  #technology .card__img-container img {
    width: 100%;
    height: 334px;
  }
  #technology .card {
    justify-content: flex-start;
    order: -1;
    height: 320px;
  }
  .num-group {
    flex-direction: row;
    height: auto;
    column-gap: 16px;
  }
  .num-group span {
    font-size: 24px;
    width: 60px;
    height: 60px;
  }
}
@media (max-width: 560px) {
  #technology .mt {
    margin-top: 12rem;
  }
  #technology .flex-center {
    row-gap: 33px;
  }
  #technology .card__img-container {
    width: 100%;
  }
  #technology .card__img-container img {
    width: 100%;
    height: 170px;
  }
  .num-group span {
    height: 40px;
    width: 40px;
    font-size: 16px;
  }
  #technology .card {
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 90%;
    height: 265px;
  }
  .card__title.md-title {
    font-size: 24px;
    line-height: normal;
    margin-bottom: 16px;
  }
  #technology .card__info {
    line-height: 25px;
    letter-spacing: 1px;
  }
}
</style>
