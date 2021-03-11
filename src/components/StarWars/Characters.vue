<template>
  <h2>Characters</h2>
  <table>
    <tr>
      <th>Name</th>
      <th>Gender</th>
      <th>Eye Color</th>
      <th>Hair Color</th>
      <th>Skin Color</th>
      <th>Height</th>
      <th>Mass</th>
      <th>Movies</th>
    </tr>
    <Character
      v-for="character in characters"
      :key="character.id"
      :character="character"
    />
  </table>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

import Character from "./Character";
export default {
  components: {
    Character
  },

  async setup() {
    const characters = ref(null);

    const response = await axios.get("https://swapi.dev/api/people/");

    const people = response.data.results.map(async actor => {
      const movies = actor.films.map(async film => {
        const movieResponse = await axios.get(film.replace("p:", "ps:"));
        return movieResponse.data.title;
      });
      await Promise.all(movies).then(res => (actor.movies = res.join(", ")));
      return actor;
    });

    await Promise.all(people).then(result => (characters.value = result));

    return {
      characters
    };
  }
};
</script>

<style>
table {
  border-collapse: collapse;
}
th,
td {
  border: 1px solid black;
  padding: 2px 6px;
}
</style>
