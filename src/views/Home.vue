<template>
  <div class="home">
    <v-autocomplete
      v-model="value"
      :items="items"
      @input="tecaj"
      dense
      filled
    ></v-autocomplete>

    <v-autocomplete
      v-model="valueDva"
      :items="items"
      @input="tecaj"
      dense
      filled
    ></v-autocomplete>

    <v-text-field
      v-model="vrijednost"
      @input="tecaj"
      label="Vrijednost"
    ></v-text-field>

    <v-text-field :value="rezultat" label="Rezultat" disabled></v-text-field>

    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">Name</th>
            <th class="text-left">Calories</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="item in items"
            :key="item.value"
            @click="prikaziDialog(item)"
          >
            <td>{{ item.value }}</td>
            <td>{{ item.text }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>

    <div class="text-center">
      <v-dialog v-model="dialog" width="500">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="red lighten-2" dark v-bind="attrs" v-on="on">
            Click Me
          </v-btn>
        </template>

        <v-card>
          <v-card-title class="headline grey lighten-2">
            {{ aktivniRedak.text }}
          </v-card-title>

          <v-divider></v-divider>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" text @click="dialog = false">
              I accept
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      items: [],
      value: "eur",
      valueDva: "bam",
      vrijednost: 1,
      rezultat: null,
      dialog: false,
      aktivniRedak: {},
    };
  },
  methods: {
    dostupneValute: function () {
      this.axios
        .get(
          "https://cdn.jsdelivr.net/gh/fawazahmed0/currency-api@1/latest/currencies.json"
        )
        .then((response) => {
          console.log(response.data);

          let items = [];

          for (const [kratica, puni_naziv] of Object.entries(response.data)) {
            items.push({ value: kratica, text: puni_naziv });
          }

          this.items = items;
        });
    },
    tecaj: function () {
      this.axios
        .get(
          `https://cdn.jsdelivr.net/gh/fawazahmed0/currency-api@1/latest/currencies/${this.value}/${this.valueDva}.json`
        )
        .then((response) => {
          console.log(response);
          this.rezultat = this.vrijednost * response.data[this.valueDva];
        });
    },
    prikaziDialog: function (item) {
      this.aktivniRedak = item;
      this.dialog = true;
    },
  },
  created() {
    this.dostupneValute();
    this.tecaj();
  },
};
</script>
