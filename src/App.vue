<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img src="@/assets/lh.png" max-width="55px" contain class="mr-3" />
        <h1>勞校中學開放日</h1>
      </div>

      <v-spacer />

      <v-img src="@/assets/70.png" max-width="55px" contain class="mr-3" />
    </v-app-bar>

    <v-main>
      <v-container fluid fill-height>
        <v-row class="align-center justify-center px-3">
          <v-col cols="12">
            <v-img
              v-for="i in [1, 2, 3, 6]"
              :key="i"
              :src="require(`@/assets/${i}.svg`)"
              contain
              eager
              v-show="i === curFloor"
            />
          </v-col>
          <v-col cols="8" class="d-flex flex-column justify-center mt-5">
            <div class="d-flex justify-space-around">
              <v-btn
                v-for="i in 6"
                :key="i"
                fab
                x-large
                :disabled="i === 4 || i === 5"
                :color="i === curFloor ? 'accent lighten-1' : 'primary'"
                class="mb-5 floor-btn"
                @click="curFloor = i"
              >
                {{ i }}
              </v-btn>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

    <v-footer app color="secondary" dark class="justify-center">
      <span>Developed by <b>Terry_CCI</b> @ 勞校中學電腦科組</span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class App extends Vue {
  private curFloor = 1;
}
</script>

<style lang="scss">
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    "微軟正黑體", Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

main {
  background: #d4f8ff;
}

.floor-btn {
  font-size: 2.5rem !important;

  .v-btn__content {
    top: -0.06em;
  }
}
</style>
