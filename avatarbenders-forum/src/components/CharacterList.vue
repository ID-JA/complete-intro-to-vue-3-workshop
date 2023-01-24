<script>
import BaseLayout from "./BaseLayout.vue";
export default {
  props: {
    characterList: {
      type: Array,
      required: true,
    },
  },
  methods: {
    addFavoriteCharacter(character) {
      console.log(character);
      this.$emit("favorite-character", character);
    },
  },
  emits: ["favorite-character"],
  components: { BaseLayout },
};
</script>

<template>
  <BaseLayout>
    <template v-slot:title>Character List</template>
    <template v-slot:content>
      <p v-if="characterList.length === 0">There are no characters</p>
      <ul>
        <li
          v-for="(character, index) in characterList"
          v-bind:key="`item--${index}`"
        >
          <p>{{ character.name }}</p>
          <button @click="addFavoriteCharacter(character)">⭐ Favorite</button>
        </li>
      </ul>
    </template>
  </BaseLayout>
</template>
