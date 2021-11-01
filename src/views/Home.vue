<template>
  <main class="mb-10" v-if="!loading">
    <div class="my-4">
      <country-select
        @get-country="getCountryData"
        :countries="countries"
      ></country-select>
      <button
        @click="clearCountryData"
        v-if="stats.Country"
        class="bg-green-700 text-white rounded p-3 my-4 focus:ouline-none hover:bg-green-600"
      >
        Clear Country
      </button>
    </div>
    <Bar :stats="stats" />
    <!-- TWO DIFFERENT WAYS TO DECLARE Components -->
    <!-- <data-title :text="title" :dataDate="dataDate"></data-title> -->
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
    <img :src="loadingImage" class="w-24 m-auto" alt="" />
  </main>
</template>

<script>
// Differnt WAYS TO Import Components...

import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import Bar from "@/components/Bar";
import CountrySelect from "../components/CountrySelect.vue";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
    Bar,
  },
  data() {
    DataTitle;
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
      loadingImage: require("../assets/hourglass.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
