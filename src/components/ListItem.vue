<template>
  <li class="database__item">
    <div class="database__tools">
      <i class="fas fa-info-circle"></i>
      <i class="fas fa-edit"></i>
      <i class="fas fa-trash-alt"></i>
    </div>
    {{ item.nickname }}

    <img :src="link[0]" class="database__img" />
  </li>
</template>

<script>
export default {
  data() {
    return {
      link: this.item.images,
    };
  },
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.database__tools {
  display: flex;
  flex-direction: column;

  i {
    cursor: pointer;
    transition: .3s ease-in;
  }

  i:nth-child(n + 2) {
    margin-top: 30px;
  }

  i:hover {
    position: relative;
    color: rgb(66, 59, 59);
    &::after {
      padding: 5px;
      position: absolute;
      font-size: 14px;
      color: rgb(73, 63, 63);
      right: -120px;
      width: 90px;
      text-align: center;
      top: 50%;
      transform: translateY(-50%);
      background: rgb(247, 217, 217);
      border-radius: 5px;
    }
  }

  i:first-child:hover {
    &::after {
      content: "Read more";
    }
  }

  i:nth-child(2):hover {
    &::after {
      content: "Edit superhero";
    }
  }

  i:last-child:hover {
    &::after {
      content: "Delete superhero";
    }
  }
}

.database__item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 200px;
  padding: 20px;
  margin: 10px 0;
  border: 1px solid black;
  border-radius: 5px;
  background: rgba(163, 204, 209, 0.164);
  font-size: 27px;
}

.database__img {
  width: 300px;
  height: 200px;
  border-radius: 8px;
}
</style>
