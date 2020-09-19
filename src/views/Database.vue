<template>
  <div class="database-block container">
    <div class="buttons">
      <router-link to="/" class="button">Back Home</router-link>
      <a class="button">Create a hero</a>
    </div>
    <BaseList v-bind:items="items" />
    <CreateForm class="create-form" />
  </div>
</template>

<script>
import BaseList from "@/components/BaseList";
import CreateForm from "@/components/CreateForm";
import superman from "@/assets/img/superman.jpg";
import batman from "@/assets/img/batman.jpg";
import spiderman from "@/assets/img/spiderman.jpg";

export default {
  data() {
    return {
      items: [
        {
          id: 1,
          nickname: "Superman",
          realName: "Clark Kent",
          originDescription:
            "he was born Kal-El on the planet Krypton, before being rocketed to Earth as an infant by his scientist father Jor-El, moments before Krypton's destruction...",
          superpowers:
            "solar energy absorption and healing factor, solar flare and heat vision, solar invulnerability, flight…",
          catchPhrase: `“Look, up in the sky, it's a bird, it's a plane, it's Superman!”`,
          images: [superman],
        },
        {
          id: 2,
          nickname: "Batman",
          realName: "Clark Kent",
          originDescription:
            "he was born Kal-El on the planet Krypton, before being rocketed to Earth as an infant by his scientist father Jor-El, moments before Krypton's destruction...",
          superpowers:
            "solar energy absorption and healing factor, solar flare and heat vision, solar invulnerability, flight…",
          catchPhrase: `“Look, up in the sky, it's a bird, it's a plane, it's Superman!”`,
          images: [batman],
        },
        {
          id: 3,
          nickname: "Spiderman",
          realName: "Clark Kent",
          originDescription:
            "he was born Kal-El on the planet Krypton, before being rocketed to Earth as an infant by his scientist father Jor-El, moments before Krypton's destruction...",
          superpowers:
            "solar energy absorption and healing factor, solar flare and heat vision, solar invulnerability, flight…",
          catchPhrase: `“Look, up in the sky, it's a bird, it's a plane, it's Superman!”`,
          images: [spiderman],
        },
      ],
    };
  },
  components: {
    BaseList,
    CreateForm,
  },
};
</script>

<style lang="scss">
.buttons {
  display: flex;
  justify-content: space-between;
}

.create-form {
  position: fixed;
  top: 35px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10;
}
</style>
