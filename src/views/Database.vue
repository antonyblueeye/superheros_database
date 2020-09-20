<template>
  <div class="database-block container">
    <div class="buttons">
      <router-link to="/" class="button">Back Home</router-link>
      <a class="button" @click="visible = !visible">Create a hero</a>
    </div>
    <BaseList
      v-bind:items="items"
      v-on:remove-item="removeItem"
      v-if="items.length > 0"
    />
    <p class="nothing-text" v-else>The database is empty</p>
    <CreateForm
      class="form-window"
      v-show="visible"
      v-on:close-form="closeForm"
      v-bind:items="items"
      @add-hero="addHero"
    />
    <ReadAbout
      class="form-window"
      v-bind:items="items"
      v-show="visibleReading"
      v-on:close-reading="closeReading"
    />
    <EditHero
      class="form-window"
      v-show="visibleEditing"
      v-bind:items="items"
      v-on:close-editing="closeEditing"
      @edit-hero="editHero"
    />
  </div>
</template>

<script>
import BaseList from "@/components/BaseList";
import CreateForm from "@/components/CreateForm";
import ReadAbout from "@/components/ReadAbout";
import EditHero from "@/components/EditHero";
import superman from "@/assets/img/superman.jpg";
import superman2 from "@/assets/img/superman-2.jpg";
import batman from "@/assets/img/batman.jpg";
import batman2 from "@/assets/img/batman-2.jpg"
import spiderman from "@/assets/img/spiderman.jpg";
import spiderman2 from "@/assets/img/spiderman-2.jpg";
import { bus } from "@/main.js";

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
          images: [superman, superman2],
        },
        {
          id: 2,
          nickname: "Batman",
          realName: "Christian Bale",
          originDescription:
            "Batman is the superhero protector of Gotham City, a man dressed like a bat who fights against evil and strikes terror into the hearts of criminals everywhere. In his public identity he is Bruce Wayne, billionaire industrialist and notorious playboy...",
          superpowers:
            "Unlike most superheroes, Batman does not possess any inhuman superpowers. He does, however, possess a genius-level intellect and is a peerless martial artist, and his vast wealth affords him an extraordinary arsenal of weaponry and equipment.…",
          catchPhrase: `“Holy...!”`,
          images: [batman, batman2],
        },
        {
          id: 3,
          nickname: "Spiderman",
          realName: "Tobias Maguire",
          originDescription:
            "Spider-Man's Powers and Abilities: Superhuman strength, agility, endurance, ability to stick to and climb walls and other surfaces, uses self-designed web-shooters allowing him to fire and swing from sticky webs, special...",
          superpowers:
            "Superhuman strength, speed, durability, agility, stamina, reflexes/reactions, coordination, balance and endurance.…",
          catchPhrase: `“With Great Power, Comes Great Responsibility”`,
          images: [spiderman, spiderman2],
        },
      ],
      visible: false,
      visibleReading: false,
      visibleEditing: false,
    };
  },
  components: {
    BaseList,
    CreateForm,
    ReadAbout,
    EditHero,
  },
  methods: {
    removeItem(id) {
      this.items = this.items.filter((t) => t.id !== id);
      console.log(this.items);
    },    
    closeForm() {
      this.visible = !this.visible;
    },
    closeReading() {
      this.visibleReading = !this.visibleReading;
    },
    closeEditing() {
      this.visibleEditing = !this.visibleEditing;
    },
    addHero(hero) {
      this.items.push(hero);
      this.visible = false;
    },
    editHero(hero) {
      this.items = this.items.filter(t => t.id !== hero.id)
      this.items.push(hero)
      this.visibleEditing = false
    }
  },
  created() {
    bus.$on("reading-info", (data) => {
      this.visibleReading = !this.visibleReading;
    });
    bus.$on("edit-info", (data) => {
      this.visibleEditing = !this.visibleEditing;
    });
  },
};
</script>

<style lang="scss">
.buttons {
  display: flex;
  justify-content: space-between;
}

.form-window {
  position: fixed;
  top: 35px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10;
}

.nothing-text {
  padding: 50px;
  text-align: center;
  font-size: 30px;
}
</style>
