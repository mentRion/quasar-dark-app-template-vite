<template>
  <q-item clickable :to="{ name: 'movies' }">
    <q-item-section avatar>
      <q-icon flat round color="teal" name="play_circle" />
    </q-item-section>

    <q-item-section>
      <q-item-label color="teal">Movies</q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "EssentialLink",
});
</script>
