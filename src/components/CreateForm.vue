<template>
  <form @submit.prevent="onSubmit" class="modal-window">
    <span class="exit" @click="$emit('close-form')"></span>
    <h4>Create a new superhero</h4>
    <label for="nickname">Nickname</label>
    <input type="text" id="nickname" v-model="nickname"/>
    <label for="real-name">Real Name</label>
    <input type="text" id="real-name" v-model="realName"/>
    <label for="origin-description">Origin Description</label>
    <textarea id="origin-description" v-model="description"></textarea>
    <label for="superpowers">Superpowers</label>
    <textarea id="superpowers" v-model="superpowers"></textarea>
    <label for="catch-phrase">Catch Phrase</label>
    <textarea id="catch-phrase" v-model="catchPhrase"></textarea>
    <label for="images">Images (paste a link)</label>
    <input type="text" id="images" v-model="imageOne"/>
    <input type="text" id="images" v-model="imageTwo"/>
    <button type="submit" class="button">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      nickname: '',
      realName: '',
      description: '',
      superpowers: '',
      catchPhrase: '',
      imageOne: '',
      imageTwo: ''
    }
  },
  props: ["items"],
  methods: {
    onSubmit() {
      const newHero = {
        id: Date.now(),
        nickname: this.nickname,
        realName: this.realName,
        originDescription: this.description,
        superpowers: this.superpowers,
        catchPhrase: this.catchPhrase,
        images: [this.imageOne, this.imageTwo] 
      }

      this.$emit('add-hero', newHero)
      this.nickname = '',
      this.realName = '',
      this.description = '',
      this.superpowers = '',
      this.catchPhrase = '',
      this.imageOne = '',
      this.imageTwo = ''
    }
  },
};
</script>

<style lang="scss">
.modal-window {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 90vh;
  width: 80%;
  background: rgb(160, 140, 140);
  border-radius: 8px;
  box-shadow: 1px 1px 15px 2px #000;
  color: aliceblue;

  h4 {
    font-size: 32px;
    text-decoration: underline;
  }

  label {
    text-transform: uppercase;
  }

  input,
  textarea {
    padding: 3px 10px;
    width: 50%;
    border: none;
    border-radius: 5px;
    font-size: 20px;
    color: rgb(75, 65, 65);
    &:focus {
      outline: none;
      box-shadow: 1px 1px 12px 2px black;
    }
  }

  input {
    height: 30px;
  }

  textarea {
    height: 60px;
    resize: none;
  }
}

.exit {
  width: 20px;
  height: 20px;
  position: absolute;
  top: 25px;
  right: 40px;
  cursor: pointer;
  &:after {
    top: 10px;
    left: -5px;
    position: absolute;
    content: "";
    width: 25px;
    height: 2px;
    background: antiquewhite;
    transform: rotate(45deg);
  }
  &:before {
    top: 10px;
    left: -5px;
    position: absolute;
    content: "";
    width: 25px;
    height: 2px;
    background: antiquewhite;
    transform: rotate(-45deg);
  }
}

.modal-window > * {
  margin: 5px;
}
</style>
