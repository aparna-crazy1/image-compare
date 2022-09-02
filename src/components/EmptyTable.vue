<template>
  <v-row>
    <v-col cols="12">
      <template>
        <v-simple-table class="mb-15" fixed-header height="100px" style="border: 1px solid #E0E0E0">
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
            <tbody style="justify-content: center">
              <tr>
                <td colspan="5" style="text-align: center">
                  No records found! Add records to compare.
                </td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </template>
    </v-col>
  </v-row>
</template>

<script>
export default {};
</script>
