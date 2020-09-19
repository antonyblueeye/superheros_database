<template>
  <form @submit.prevent="onSubmit" class="form-to-create">
    <span class="exit"></span>
    <h4>Create a new superhero</h4>
    <label for="nickname">Nickname</label>
    <input type="text" id="nickname" />
    <label for="real-name">Real Name</label>
    <input type="text" id="real-name" />
    <label for="origin-description">Origin Description</label>
    <textarea id="origin-description"></textarea>
    <label for="superpowers">Superpowers</label>
    <textarea id="superpowers"></textarea>
    <label for="catch-phrase">Catch Phrase</label>
    <textarea id="catch-phrase"></textarea>
    <label for="images">Images</label>
    <input type="text" id="images" />
    <button type="submit" class="button">Create</button>
  </form>
</template>

<script>
export default {};
</script>

<style lang="scss">
.form-to-create {
  display: none;
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

  .exit {
    position: absolute;
    top: 25px;
    right: 40px;
    cursor: pointer;
    &:after {
      position: absolute;
      content: "";
      width: 25px;
      height: 2px;
      background: antiquewhite;
      transform: rotate(45deg);
    }
    &:before {
      position: absolute;
      content: "";
      width: 25px;
      height: 2px;
      background: antiquewhite;
      transform: rotate(-45deg);
    }
  }
}

.form-to-create > * {
  margin: 5px;
}
</style>
