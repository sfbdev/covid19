﻿<template>
  <div>
    <client-only>
      <Linec type="line" :options="options" :series="series" />
    </client-only>
  </div>
</template>

<script>
import { mapState, mapActions, mapGetters } from "vuex";
export default {
  components: {
    Linec: () => import("vue-apexcharts")
  },
  data() {
    return {
      options: {
        colors: ["#feb72b"],
        chart: {
          id: "vuechart-example"
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
        }
      },
      series: [
        {
          name: "series-1",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        }
      ]
    };
  },

  computed: {},

  methods: {}
};
</script>
