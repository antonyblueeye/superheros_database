<template>
  <div class="home container">
    <div class="home__description">
      <h3 class="home__title">What is it about?</h3>
      <p class="main-text">
        This application is a Vue.js based Database that allows you to manage
        different superheros you like. You can add your superhero, delete
        superheros you don't like and change some information about any
        superhero.
      </p>
      <router-link to="/database" class="button">Explore it</router-link>
    </div>
    <img
      src="./../assets/img/superheros.jpg"
      alt="Superheros"
      class="home__superheros-img"
    />
  </div>
</template>

<script>
// @ is an alias to /src

export default {};
</script>

<style lang="scss">
.main-text {
  font-size: 20px;
  line-height: 30px;
}

.home {
  display: grid;
  grid-template-columns: 1fr 1fr;

  &__title {
    font-size: 30px;
    font-weight: 700;
  }

  &__description {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    p {
      margin-top: 20px;
    }
  }

  &__superheros-img {
    width: 100%;
  }
}

.button {
  display: block;
  text-align: center;
  width: 200px;
  line-height: 40px;
  margin-top: 20px;
  font-size: 25px;
  border: 1px solid black;
  color: rgb(56, 50, 50);
  border-radius: 13px;
  transition: 0.3s ease-in;
  cursor: pointer;

  &:hover {
    color: #fff;
    background: rgb(56, 50, 50);
  }

  &:focus {
    outline: none;
  }
}
</style>
