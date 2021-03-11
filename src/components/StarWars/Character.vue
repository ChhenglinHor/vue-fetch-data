<template>
  <tr>
    <td>{{ character.name }}</td>
    <td>{{ character.gender }}</td>
    <td>{{ character.eye_color }}</td>
    <td>{{ character.hair_color }}</td>
    <td>{{ character.skin_color }}</td>
    <td>{{ character.height }}</td>
    <td>{{ character.mass }}</td>
    <td>{{ character.movies }}</td>
  </tr>
</template>

<script>
export default {
  props: {
    character: Object
  }
};
</script>
