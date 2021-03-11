<template>
  <h1>Star War Actors Info</h1>

  <div v-if="errMsg">{{ errMsg }}</div>
  <Suspense v-else>
    <template #default>
      <Characters />
    </template>
    <template #fallback>
      <div>Loading ...</div>
    </template>
  </Suspense>
</template>

<script>
import { onErrorCaptured, ref } from "vue";
import Characters from "./Characters";

export default {
  components: {
    Characters
  },

  setup() {
    const errMsg = ref(null);

    onErrorCaptured(() => {
      errMsg.value = "Something went wrong";
    });

    return {
      errMsg
    };
  }
};
</script>
