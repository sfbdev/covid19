﻿<template>
  <div class="mt-2">
    <client-only>
      <Pie type="donut" :options="options" :series="series" />
    </client-only>
  </div>
</template>

<script>
import axios from "axios";
import { mapState, mapActions, mapGetters } from "vuex";

export default {
  components: {
    Pie: () => import("vue-apexcharts")
  },
  data() {
    return {
      totalData: [],
      options: {},
      series: [44, 55, 41, 17, 15]
    };
  },

  computed: {
		...mapState(["data"]),
		...mapGetters(),

    totalCase: function() {
      let data = this.data.map(country => {
        return country.cases.total;
      });
      var sum = 0;
      for (var i = 0; i < data.length; i++) {
        sum += data[i];
      }
      return sum / 2;
    }
  },

  mounted() {
    this.apiData();
  },

  methods: {
    ...mapActions(["apiData"])
  }
};
</script>
