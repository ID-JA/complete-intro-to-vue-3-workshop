<script>
export default {
  props: {
    favoriteList: {
      type: Array,
      required: true,
    },
  },
};
</script>

<template>
  <h2>Favorite Characters</h2>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" v-bind:key="`item-${index}`">
      {{ character }}
    </li>
  </ul>
  <p v-else>No favorite characters yet!</p>
</template>
