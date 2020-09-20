<template>
    <form @submit.prevent="onSubmit" class="modal-window">
        <span class="exit" @click="$emit('close-editing')"></span>
        <h4>Edit a superhero</h4>
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
        <button type="submit" class="button">Edit</button>
    </form>
</template>

<script>
import { bus } from "./../main";

export default {
    data() {
        return {
            id: 0,
            nickname: '',
            realName: '',
            description: '',
            superpowers: '',
            catchPhrase: '',
            imageOne: '',
            imageTwo: ''
        }
    },
    props: ['items'],
    methods: {
        onSubmit() {
            const editedHero = {
                id: this.id,
                nickname: this.nickname,
                realName: this.realName,
                originDescription: this.description,
                superpowers: this.superpowers,
                catchPhrase: this.catchPhrase,
                images: [this.imageOne, this.imageTwo] 
            }
                this.$emit('edit-hero', editedHero)
                console.log(editedHero)
        }
    },
    created() {
        bus.$on("edit-info", (data) => {
            this.newItems = this.items.filter(t => t.id === data)
            this.id = this.newItems[0].id
            this.nickname = this.newItems[0].nickname
            this.realName = this.newItems[0].realName
            this.description = this.newItems[0].originDescription
            this.superpowers = this.newItems[0].superpowers
            this.catchPhrase = this.newItems[0].catchPhrase
            this.imageOne = this.newItems[0].images[0]
            this.imageTwo = this.newItems[0].images[1]
        });
  },
}
</script>

<style lang="scss">

</style>