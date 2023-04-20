<template>
  <!-- <div class="row q-col-gutter-lg q-pa-lg"> -->
  <div class="col-xs-12 col-sm-4 col-md-4 col-lg-4">
    <q-card class="my-card" flat>
      <q-img :src="image" height="200px"> </q-img>
      <q-card-section style="height: 300px; overflow: hidden">
        <div class="text-subtitle2">{{ year }}</div>
        <div class="text-h6">{{ title }}</div>
        <q-rating v-model="stars" :max="rating" />
        <div class="text-subtitle2">{{ writers }}</div>
        <div class="text-subtitle2">{{ director }}</div>
        <div class="text-subtitle2">
          {{ description }}
        </div>
      </q-card-section>
      <q-card-actions align="right">
        <q-btn flat round color="red" icon="favorite" />
        <q-btn flat round color="teal" icon="bookmark" />
        <q-btn flat round color="primary" icon="share" />
        <q-btn flat round color="primary" icon="play_circle" />
      </q-card-actions>
    </q-card>
  </div>
  <!-- </div> -->
</template>

<script>
import { defineComponent } from "vue";
import { ref } from "vue";

export default defineComponent({
  name: "ItemCard",
  props: {
    rank: {
      type: String,
      default: "",
    },
    title: {
      type: String,
      default: "",
    },
    description: {
      type: String,
      default: "",
    },
    writers: {
      type: String,
      default: "",
    },
    director: {
      type: String,
      default: null,
    },
    year: {
      type: Number,
      default: 0,
    },
    trailer: {
      type: String,
      default: "",
    },
    image: {
      type: String,
      default: "",
    },
    rating: {
      type: String,
      default: "",
    },
  },
  setup() {
    let stars = ref(8);
    return { stars };
  },
});
</script>
