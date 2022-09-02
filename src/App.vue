<template>
  <v-app>
    <v-app-bar app absolute color="#fff" dark>
      <div class="d-flex align-center">
        <span style="color: #000">IMAGE COMPARE</span>
      </div>
    </v-app-bar>
    <v-main>
      <Compare />
      <!-- <Pagination /> -->
    </v-main>
  </v-app>
</template>

<script>
import Compare from "./components/Compare";
// import Pagination from "./components/Pagination/Pagination";
export default {
  name: "App",
  components: {
    Compare,
    // Pagination
  },
  data() {
    return {
      title: "Image Compare",
    };
  },
  created() {
    document.title = this.title;
  },
};
</script>

<style>
.v-toolbar__content, .v-toolbar__extension{
  text-align: center;
  justify-content: center;
}
</style>
