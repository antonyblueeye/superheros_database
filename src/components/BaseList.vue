<template>
  <ul class="database">
    <ListItem
      v-for="(item, i) of items"
      v-show="i < 5 + num"
      v-bind:item="item"
      :key="item.name"
      v-on:remove-item="removeItem"
    />
    <button
      v-if="items.length - 5 - num > 0"
      class="button show-more-btn"
      @click="showMoreHeroes"
    >
      See other {{ items.length - 5 - num }} heroes
    </button>
  </ul>
</template>

<script>
import ListItem from "@/components/ListItem";

export default {
  data() {
    return {
      num: 0,
    };
  },
  props: ["items"],
  components: {
    ListItem,
  },
  methods: {
    removeItem(id) {
      this.$emit("remove-item", id);
    },
    showMoreHeroes() {
      this.num += this.items.length - 5;
    },
  },
};
</script>

<style scoped lang="scss">
.database {
  margin: 20px 0;
}

.show-more-btn {
  width: 300px;
  margin: 40px auto;
}
</style>
