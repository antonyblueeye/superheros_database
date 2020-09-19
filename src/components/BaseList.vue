<template>
  <ul class="database">
    <ListItem 
        v-for="(item, i) of items" 
        v-show="i < 5"
        v-bind:item="item"
        :key="item.name"
    />
  </ul>
</template>

<script>
import ListItem from '@/components/ListItem'

export default {
    props: ['items'],
    components: {
        ListItem
    }
};
</script>

<style scoped lang="scss">
.database { 
    margin: 20px 0;
}
</style>
