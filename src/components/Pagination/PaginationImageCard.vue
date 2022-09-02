<template>
  <v-hover>
    <template>
      <v-card class="mx-auto" max-width="344">
        <v-img :lazy-src="imageData.url" :src="imageData.url"></v-img>
        <v-card-text>
          <h2 class="text-h6 primary--text">
            <div>
              {{ imageData.title.substring(0, 10) }}
            </div>
          </h2>
          <div>
            <span><strong>ID - {{ imageData.id }}</strong></span>
          </div>
          <div>
            <span>{{ imageData.url }}</span>
          </div>
        </v-card-text>
      </v-card>
    </template>
  </v-hover>
</template>

<script>
export default {
  name: "ImageComparison",
  data() {
    return {};
  },
  props: {
    imageData: {
      type: Object,
      default: null,
    },
  },
  methods: {},
};
</script>
