<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-secondary">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <!--  -->
        </q-toolbar-title>

        <div>
          <!--  -->
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item>
          <q-item-section style="height: 150px">
            <q-img
              class="absolute-top"
              src="../assets/background/sl_121019_25870_38.jpg"
              style="height: 150px"
            >
              <div class="absolute-bottom bg-transparent">
                <q-avatar size="56px" class="q-mb-sm">
                  <!-- <img src="https://cdn.quasar.dev/img/boy-avatar.png" /> -->
                </q-avatar>
                <div class="text-weight-bold">Movie Haus</div>
              </div>
            </q-img>
          </q-item-section>

          <q-item-label header fit> Essential Links </q-item-label>

          <q-item-section>
            <q-item-label>title</q-item-label>
            <q-item-label caption>caption</q-item-label>
          </q-item-section>
        </q-item>

        <EssentialLink />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
