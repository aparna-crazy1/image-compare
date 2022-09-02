<template>
  <v-hover>
    <template v-slot:default="{ hover }">
      <v-card class="mx-auto" max-width="344">
        <v-img :lazy-src="imageData.url" :src="imageData.url"></v-img>
        <v-card-text>
          <h2 class="text-h6 primary--text">
            <div>
              {{ imageData.title.substring(0, 10) }}
            </div>
          </h2>
          <div>
            <span v-show="showAddToCompareBtn"
              ><strong> Compare - ID - {{ imageData.id }}</strong></span
            >
            <span v-show="showRemoveFromCompareBtn"
              ><strong> Remove - ID - {{ imageData.id }}</strong></span
            >
          </div>
          <div>
            <span>{{ imageData.url }}</span>
          </div>
        </v-card-text>
        <v-card-title
          style="justify-content: center"
          v-if="$vuetify.breakpoint.smAndDown"
        >
          <v-btn
            v-show="showAddToCompareBtn"
            @click="addToCompare(imageData.id)"
            >Compare</v-btn
          >
          <v-btn
            v-show="showRemoveFromCompareBtn"
            @click="removeFromCompare(imageData.id)"
            >Remove</v-btn
          >
        </v-card-title>
        <v-fade-transition v-if="$vuetify.breakpoint.mdAndUp">
          <v-overlay v-if="hover" absolute color="#036358">
            <v-btn
              v-show="showAddToCompareBtn"
              @click="addToCompare(imageData.id)"
              >Compare</v-btn
            >
            <v-btn
              v-show="showRemoveFromCompareBtn"
              @click="removeFromCompare(imageData.id)"
              >Remove</v-btn
            >
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
</template>

<script>
export default {
  name: "ImageComparison",
  data() {
    return {
      overlay: false,
      showAddToCompareBtn: true,
      showRemoveFromCompareBtn: false,
    };
  },
  props: {
    imageData: {
      type: Object,
      default: null,
    },
  },
  methods: {
    addToCompare(id) {
      this.showAddToCompareBtn = false;
      this.showRemoveFromCompareBtn = true;
      this.$emit("addToCompare", id);
    },
    removeFromCompare(id) {
      this.showRemoveFromCompareBtn = false;
      this.showAddToCompareBtn = true;
      this.$emit("removeFromCompare", id);
    },
  },
};
</script>
