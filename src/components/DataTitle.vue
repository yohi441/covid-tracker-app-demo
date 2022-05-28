<template>
  <div class="flex flex-col items-center justify-center mb-3 space-y-2 text-sm sm:mb-5">
    <div class="flex items-center justify-center px-3 py-2 text-gray-800 rounded-sm shadow-sm bg-green-50">Last Updated: {{ timestamp }}</div>
    <h2 class="text-2xl sm:text-3xl">{{ text }}</h2>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
  computed: {
    timestamp: function () {
      return moment(this.dataDate).format("MMMM Do YYYY, h:mm:ss a");
    },
  },
};
</script>
