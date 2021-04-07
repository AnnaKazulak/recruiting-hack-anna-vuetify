<template>
  <v-app id="app">
    <h1 class="ml-16 mt-5 white--text">Systemübersicht</h1>
    <v-card class="mx-16">
      <v-card-title>
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Suchen"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="json"
        :search="search"
        class="primary--text"
      >
        <template v-slot:header.name="{ header }">
          {{ header.text.toUpperCase() }}
        </template>

        <template v-slot:item.url="{ item }">
          <a :href="item.url">{{ item.url }}</a>
        </template>
      </v-data-table>
    </v-card>
  </v-app>
</template>

<script>
import Kunden from "./assets/kunden.json";
export default {
  name: "App",

  components: {},

  data: () => ({
    search: "",
    json: Kunden,
    headers: [
      {
        text: "Kundenname",
        align: "start",
        sortable: true,
        value: "name",
      },
      { text: "Externe URL", value: "url", sortable: false },
      { text: "Login Seite", value: "login", sortable: false },
    ],
    //
  }),
};
</script>

<style lang="css">
#app {
  background-color: #003a5d;
}
</style>
