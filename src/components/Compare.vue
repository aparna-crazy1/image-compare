<!-- 
  Compare.vue
  Included in App.vue
  It contains the image list and comparison table 
-->
<template>
  <v-layout>
    <v-container>
      <v-row class="mt-2" :class="{ 'justify-center': isCenterAligned }">
        <v-col
          cols="12"
          sm="3"
          md="2"
          v-for="(profile, index) of imageList"
          :key="index"
        >
          <ImageCard
            :imageData="profile"
            @addToCompare="addToCompareId"
            @removeFromCompare="removeFromCompareId"
          />
        </v-col>
      </v-row>
      <div class="mt-6 mb-3" style="text-align: center">COMPARISON TABLE</div>
      <ComparisonTable v-if="hasDataToCompare" :tableData="comparisonArray" />
      <EmptyTable v-if="!hasDataToCompare" />
    </v-container>
  </v-layout>
</template>

<script>
import ImageCard from "./ImageCard";
import ComparisonTable from "./ComparsionTable";
import EmptyTable from "./EmptyTable";
export default {
  name: "ImageComparison",
  components: {
    ImageCard,
    ComparisonTable,
    EmptyTable,
  },
  data() {
    return {
      imageList: [],
      overlay: false,
      showAddToCompareBtn: true,
      showRemoveFromCompareBtn: false,
      comparisonArray: [],
    };
  },
  created() {
    // fetch the image list
    this.$http
      .get("https://jsonplaceholder.typicode.com/photos", {
        params: {
          _limit: 6, // this can be changed as needed
        },
      })
      .then((response) => {
        this.imageList = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  computed: {
    // check if table data array in not empty
    hasDataToCompare() {
      return this.comparisonArray.length > 0;
    },
    isCenterAligned() {
      return this.imageList.length < 6;
    },
  },
  methods: {
    // add image to table data array
    addToCompareId(id) {
      let imageAdded = this.imageList.filter(function (image) {
        if (image.id === id) return image;
      });
      this.comparisonArray.push(imageAdded[0]);
    },
    // remove image from table data array
    removeFromCompareId(id) {
      this.comparisonArray.splice(
        this.comparisonArray.findIndex((a) => a.id === id),
        1
      );
    },
  },
};
</script>
