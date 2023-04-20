<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="q-pa-lg flex flex-center">
    <q-pagination :v-model="model" :max="max" />
  </div>
</template>

<script>
import { ref } from "vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "MoviePagination",
  props: ["max", "model"],
});
</script>
