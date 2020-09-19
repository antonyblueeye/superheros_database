<template>
  <div id="app">
    <h1 class="main-title">
      Superhero Database Application <i class="fas fa-mask"></i> 
    </h1>
    <router-view />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Kufam:wght@500;700&family=Raleway&display=swap");
@import url("../node_modules/normalize.scss/normalize.scss");
@import url("./assets/scss/base.scss");
@import url("./assets/scss/_mixins.scss");

#app {
  .main-title {
    padding: 30px 0;
    font-family: "Kufam", cursive;
    font-weight: 700;
    color: rgb(61, 58, 58);
    text-align: center;
    position: relative;
    background: linear-gradient(
      90deg,
      rgba(245, 224, 224, 1) 0%,
      rgba(255, 231, 231, 1) 42%,
      rgba(255, 246, 246, 1) 79%
    );

    &::after {
      position: absolute;
      content: "";
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 100%;
      height: 1px;
      background: rgb(51, 48, 48);
    }

    i {
      color: rgb(48, 46, 40);
    }
  }
}
</style>
