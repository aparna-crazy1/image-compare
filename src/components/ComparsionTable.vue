<template>
  <v-row class="mb-15">
    <v-col cols="12">
      <template>
        <v-simple-table fixed-header height="auto" style="border: 1px solid #E0E0E0">
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left"></th>
                <th class="text-left">Image</th>
                <th class="text-left">ID</th>
                <th class="text-left">Title</th>
                <th class="text-left">URL</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, index) in tableData" :key="index">
                <td>Photo {{ index + 1 }}</td>
                <td>
                  <v-img
                    :src="item.url"
                    max-height="50"
                    max-width="50"
                    contain
                    class="ma-2"
                  ></v-img>
                </td>
                <td>{{ item.id }}</td>
                <td>{{ item.title }}</td>
                <td>{{ item.url }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </template>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "ImageComparison",
  props: {
    tableData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
