<template>
  <v-layout>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          sm="3"
          md="2"
          v-for="(card, index) in cardsOfCurrPage"
          :key="index"
        >
          <PaginationImageCard
            :imageData="card"
            @addToCompare="addToCompareId"
            @removeFromCompare="removeFromCompareId"
          />
        </v-col>
      </v-row>
      <v-row style="justify-content: center">
        <div>
          <a class="badge" @click="gotoPrev()">Prev</a> - {{ pageIndex + 1 }} - <a
            class="badge"
            @click="gotoNext()"
            >Next</a
          >
        </div>
      </v-row>
    </v-container>
  </v-layout>
</template>

<script>
import PaginationImageCard from "./PaginationImageCard";
export default {
  name: "ImageComparison",
  components: {
    PaginationImageCard
  },
  data() {
    return {
      cards: [],
      overlay: false,
      showAddToCompareBtn: true,
      showRemoveFromCompareBtn: false,
      comparisonArray: [],
      pageSize: 6,
      pageIndex: 0,
    };
  },
  created() {
    this.$http
      .get("https://jsonplaceholder.typicode.com/photos", {
        params: {
          _limit: 100,
        },
      })
      .then((response) => {
        this.cards = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  computed: {
    hasDataToCompare() {
      return this.comparisonArray.length > 0;
    },
    pages: function () {
        if(this.cards.length % this.pageSize === 0) 
            return Math.floor(this.cards.length / this.pageSize);
        else
            return Math.floor(this.cards.length / this.pageSize) + 1;
    },
    cardsOfCurrPage: function () {
      return this.cards.slice(
        this.pageSize * this.pageIndex,
        this.pageSize * (this.pageIndex + 1)
      );
    },
  },
  methods: {
    gotoPrev: function () {
      if (this.pageIndex > 0) this.pageIndex -= 1;
    },
    gotoNext: function () {
      if(this.pageIndex < (this.pages - 1)) this.pageIndex += 1;
    },
    addToCompareId(id) {
      let imageAdded = this.cards.filter(function (image) {
        if (image.id === id) return image;
      });
      this.comparisonArray.push(imageAdded[0]);
    },
    removeFromCompareId(id) {
      this.comparisonArray.splice(
        this.comparisonArray.findIndex((a) => a.id === id),
        1
      );
    },
  },
};
</script>
