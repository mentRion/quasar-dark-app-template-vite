<template>
  <q-page>
    <div style="height: 100vh">
      <div class="col-12">
        <q-card class="my-card" flat>
          <q-img
            src="../../assets/background/assortment-cinema-elements-red-background-with-copy-space.jpg"
            height="200px"
          >
            <div class="text-subtitle2 absolute-bottom text-left">
              <div class="text-h6">Amet consectetur adipisicing elit</div>
              <div class="text-subtitle2">
                Lorem ipsum dolor sit, amet consectetur adipisicing elit.
              </div>
            </div>
          </q-img>
        </q-card>
      </div>

      <div class="row q-col-gutter-lg q-pa-lg">
        <div class="col-2">
          <q-btn
            class="full-width q-pa-lg"
            flat
            transparent
            @click="reloadPage()"
          >
            <q-icon name="refresh" size="35px"></q-icon>
          </q-btn>
        </div>

        <div class="col-8">
          <form @submit="search()">
            <q-input v-model="textSearch" label="Search" />
          </form>
        </div>

        <div class="col-2">
          <q-btn class="full-width q-pa-lg" flat @click="search()">
            <q-icon name="search" size="35px"></q-icon>
          </q-btn>
        </div>
      </div>

      <div class="row q-col-gutter-lg q-pa-lg" style="min-height: 500px">
        <div class="full-width full-width text-center">
          <h6 v-if="movies.length === 0" class="q-ma-auto">
            Nothing to Search.
          </h6>
        </div>

        <ItemCard
          v-for="movie in movies"
          :key="movie.id"
          :title="movie.title"
          :description="movie.description"
          :year="movie.year"
          :image="movie.image"
          :rating="movie.rating"
          :director="`${movie.director.toString()}`"
        />
      </div>
      <div class="q-pa-lg flex flex-center">
        <!-- <q-pagination
        v-model="current"
        :max="max"
        @update:model-value="loadPage()"
      /> -->
        <q-btn label="All" @click="reloadPage()" />

        <q-pagination
          v-model="current"
          :max="max"
          :max-pages="maxPage"
          direction-links
          flat
          color="grey"
          active-color="primary"
          @update:model-value="loadPage()"
        />
      </div>

      <div class="col-12 mt-auto">
        <q-card class="my-card" flat>
          <q-img
            src="../../assets/background/top-view-movie-reels-with-copy-space.jpg"
          >
            <div class="text-subtitle2 absolute-bottom text-left">
              <div class="text-h6">Amet consectetur adipisicing elit</div>
              <div class="text-subtitle2">
                Lorem ipsum dolor sit, amet consectetur adipisicing elit.
              </div>
            </div>
          </q-img>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import ItemCard from "../../components/ItemCard.vue";
import { fetchedMovies } from "./scripts/response.js";

import axios from "axios";

import { ref } from "vue";

export default defineComponent({
  name: "MoviePage",
  components: {
    ItemCard,
  },
  setup() {
    const options = {
      method: "GET",
      headers: {
        "X-RapidAPI-Key": "3c40cb4382msh2088e193290ca66p1be983jsn997f71d92eec",
        "X-RapidAPI-Host": "imdb-top-100-movies.p.rapidapi.com",
      },
    };

    // const apiKey = "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";
    // const dataJson = {
    //   method: "POST",
    //   headers: {
    //     "Content-Type": "application/json",
    //     Authorization: `Bearer ${apiKey}`,
    //   },
    //   body: JSON.stringify({
    //     model: "text-davinci-003",
    //     prompt: "Isa kang Filipino student\n\nHuman: Kumusta ka na?\nAi:",
    //     temperature: 0.7,
    //     max_tokens: 256,
    //     top_p: 1,
    //     frequency_penalty: 0,
    //     presence_penalty: 0,
    //   }),
    // };

    // fetch("https://api.openai.com/v1/completions", dataJson)
    //   .then((response) => response.json())
    //   .then((data) => {
    //     console.log(data.choices);
    //   });

    // axios
    //   .post(
    //     "https://api.openai.com/v1/completions",
    //     {
    //       model: "text-davinci-003",
    //       prompt: "Isa kang Filipino student\n\nHuman: Kumusta ka na?\nAi:",
    //       temperature: 0.7,
    //       max_tokens: 256,
    //       top_p: 1,
    //       frequency_penalty: 0,
    //       presence_penalty: 0,
    //     },
    //     {
    //       headers: {
    //         "Content-Type": "application/json",
    //         Authorization: `Bearer ${apiKey}`,
    //       },
    //     }
    //   )
    //   .then((response) => response.data)
    //   .then((data) => console.log(data.choices[0].text))
    //   .catch((error) => {
    //     console.error("Error:", error);
    //   });

    let movies = ref([]);

    // fetch("https://imdb-top-100-movies.p.rapidapi.com/", options)
    //   .then((response) => response.json())
    //   .then((response) => (movies.value = response))
    //   .then(() => console.log(movies.value))
    //   .catch((err) => console.error(err));

    let max = ref(null);
    let maxPage = ref(6);
    let current = ref(1);
    let start;
    let end;
    let movieTemp = fetchedMovies.value;

    const loadPage = () => {
      max.value = movieTemp.length / 9;
      start = current.value * 9 - 9 + 1;
      end = current.value * 9 + 1;
      movies.value = movieTemp.slice(start, end);
      // alert(`${start} ${end}`);
    };

    const reloadPage = () => {
      movieTemp = fetchedMovies.value;
      max.value = movieTemp.length / 9;
      start = current.value * 9 - 9 + 1;
      end = current.value * 9 + 1;
      movies.value = movieTemp.slice(start, end);
    };

    //Image by <a href="https://www.freepik.com/free-photo/top-view-movie-reels-with-copy-space_6633592.htm#query=film%20background&position=8&from_view=keyword&track=ais">Freepik</a>
    //r
    //Image by <a href="https://www.freepik.com/free-photo/assortment-cinema-elements-red-background-with-copy-space_7089700.htm#query=film%20background&position=2&from_view=keyword&track=ais">Freepik</a>

    let textSearch = ref("");

    const search = () => {
      movies.value = null;
      movieTemp = [];
      let len = fetchedMovies.value.length;

      for (let i = 0; i < len; i++) {
        let temp = fetchedMovies.value[i];
        temp = temp.title.toLowerCase();
        console.log(temp);

        if (temp.includes(textSearch.value.toLowerCase())) {
          movieTemp.push(fetchedMovies.value[i]);

          console.log(
            `${temp},
            ${textSearch.value.toLowerCase()}`,
            fetchedMovies.value[i]
          );
        }
      }
      console.log(movieTemp);

      current.value = 1;
      start = current.value * 9 - 9;
      end = current.value * 9 + 1;
      movies.value = movieTemp.slice(start, end);
      max.value = movieTemp.length / 9;
      // movies.value = movieTemp;
    };

    loadPage();

    return {
      movies,
      max,
      current,
      loadPage,
      maxPage,
      start,
      end,
      textSearch,
      search,
      reloadPage,
    };
  },
  mounted() {},
});
</script>
