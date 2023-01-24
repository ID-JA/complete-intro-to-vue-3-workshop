<script>
import CharacterList from "./components/CharacterList.vue";
import FavoriteCharacters from "./components/FavoriteCharacters.vue";

export default {
  data: () => ({
    newCharacter: {
      name: "",
    },
    characterList: [
      {
        name: "Aang",
      },
      {
        name: "Zuko",
      },
      {
        name: "Toph",
      },
      {
        name: "Katara",
      },
    ],
    favoriteList: [],
  }),
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter);
      this.newCharacter = { name: "" };
    },
    favoriteCharacter(character) {
      this.favoriteList.push(character);
    },
  },
  components: { FavoriteCharacters, CharacterList },
};
</script>

<template>
  <div>
    <CharacterList
      :characterList="characterList"
      @favorite-character="favoriteCharacter"
    />
    <FavoriteCharacters :favoriteList="favoriteList" />
    <h2>New Character</h2>
    <pre>{{ newCharacter }}</pre>
    <label for="character-name">Name</label>
    <input
      type="text"
      v-model="newCharacter.name"
      @keyup.enter="addNewCharacter"
    />
    <span
      v-for="(character, index) in characterList"
      v-bind:key="`character-${index}`"
      >{{ character.name }}{{ index === characterList.length - 1 ? "" : ", " }}
    </span>
  </div>
</template>
