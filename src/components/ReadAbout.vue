<template>
  <div class="superhero-info modal-window">
    <span class="exit" @click="$emit('close-reading')"></span>
    <h4>Information</h4>
    <p>
      <strong>Nickname:</strong>
      {{ newItems[id].nickname }}
    </p>
    <p>
      <strong>Real Name:</strong>
      {{ newItems[id].realName }}
    </p>
    <p>
      <strong>Origin description:</strong>
      {{ newItems[id].originDescription }}
    </p>
    <p>
      <strong>Superpowers:</strong>
      {{ newItems[id].superpowers }}
    </p>
    <p>
      <strong>Catch phrase:</strong>
      {{ newItems[id].catchPhrase }}
    </p>
    <p>
      <strong>Images:</strong>
      <span v-for="el of newItems[id].images">
        <img :src="el" class="information-image" />
      </span>
    </p>
  </div>
</template>

<script>
import { bus } from "./../main";

export default {
  data() {
    return {
      newItems: [],
      id: 0,
    };
  },
  props: ["items"],
  created() {
    bus.$on("reading-info", (data) => {
      this.newItems = this.items.filter(t => t.id === data)
    //   console.log(this.newItems)
    //   this.id = data - 1;
    //   this.link = this.items[data - 1].images;
    });
  },
};
</script>

<style lang="scss">
.superhero-info {
  padding: 0 20px;
  p {
    padding: 5px;
    width: 100%;
    font-style: italic;
    font-size: 25px;

    strong {
      text-transform: uppercase;
      text-decoration: underline;
      font-style: normal;
      color: bisque;
    }

    &:last-child {
      display: flex;
      align-items: center;
      justify-content: space-around;
    }
  }
}

.information-image {
  width: 350px;
  height: 250px;
}
</style>
