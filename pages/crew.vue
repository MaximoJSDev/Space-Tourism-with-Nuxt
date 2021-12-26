<template>
  <main id="crew">
    <h2 class="title-section"><span>02</span> Pick your crew</h2>
    <div class="flex-center mt" v-if="crew !== undefined && crew.length !== 0">
      <div class="card-container">
        <article class="card">
          <h1 class="card__job">{{ crew[i].role }}</h1>
          <h3 class="card__title md-title">{{ crew[i].name }}</h3>
          <p class="card__info">
            {{ crew[i].bio }}
          </p>
        </article>
        <div class="container-points">
          <div class="points active" @click="changeRole(0)"></div>
          <div class="points" @click="changeRole(1)"></div>
          <div class="points" @click="changeRole(2)"></div>
          <div class="points" @click="changeRole(3)"></div>
        </div>
      </div>
      <div class="card__img-container">
        <img :src="require(`~/${crew[i].images.png}`)" :alt="crew[i].name" />
      </div>
    </div>
  </main>
</template>

<script>
export default {
  head() {
    return {
      title: 'Space Tourism - Crew',
    }
  },
  data() {
    return {
      crew: [],
      i: 0,
    }
  },
  methods: {
    changeRole(index) {
      console.log(index)
      let points = document.querySelectorAll('.points')
      points.forEach((activos) => {
        activos.classList.remove('active')
      })
      points[index].classList.add('active')
      this.i = index
    },
  },
  created() {
    fetch('data.json')
      .then((res) => res.json())
      .then((data) => (this.crew = data.crew))
  },
}
</script>

<style>
#crew {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  flex-direction: column;
  background: #0b0d17 url('~assets/crew/background-crew-desktop.jpg') no-repeat;
  background-size: cover;
  background-position: bottom;
  color: #fff;
  overflow: hidden;
}
#crew .card {
  position: relative;
  width: 614px;
  height: 460px;
}
#crew .card__job {
  font-family: 'Bellefair', serif;
  font-size: 32px;
  line-height: 37px;
  letter-spacing: 1px;
  font-weight: normal;
  text-transform: uppercase;
  mix-blend-mode: normal;
  opacity: 0.5;
  margin-bottom: 15px;
}
#crew .card__info {
  width: 444px;
  margin-bottom: 100px;
}
.container-points {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  column-gap: 24px;
}
.points {
  width: 15px;
  height: 15px;
  background: #ffffff;
  opacity: 0.17;
  border-radius: 50%;
  cursor: pointer;
}
.points.active {
  opacity: 1;
}
.card__img-container img {
  height: 680px;
  max-width: 600px;
  margin-bottom: -10px;
}
@media (max-width: 1220px) {
  #crew .flex-center {
    flex-direction: column;
    row-gap: 40px;
  }
  #crew .mt {
    margin-top: 12rem;
  }
  #crew .card {
    align-items: center;
    text-align: center;
    height: 325px;
  }
  #crew .card__job {
    font-size: 24px;
    margin-bottom: 8px;
  }
  #crew .card__title.md-title {
    font-size: 40px;
    line-height: 46px;
    margin-bottom: 16px;
  }
  #crew .card__info {
    font-size: 16px;
    margin-bottom: 0;
    width: 85%;
  }
  .container-points {
    width: 100%;
    justify-content: center;
  }
  .card__img-container img {
    height: 455px;
  }
}
@media (max-width: 560px) {
  #crew .flex-center {
    flex-direction: column-reverse;
    row-gap: 68px;
    padding-bottom: 20px;
  }
  #crew .card {
    width: 95%;
    justify-content: center;
    height: 325px;
  }
  #crew .card__img-container {
    width: 87%;
    border-bottom: 2px solid #53576d87;
  }
  #crew .card__img-container img {
    display: block;
    margin: 0 auto;
    height: 323px;
  }
  #crew .card-container {
    width: 100%;
    display: flex;
    align-items: center;
    flex-direction: column-reverse;
  }
  .container-points {
    margin-bottom: 1.8rem;
  }
  #crew .card__info {
    font-size: 15px;
  }
}
</style>
