<template>


  <div class="flex justify-center mb-5">
    <select class="w-full transition duration-150 ease-in-out rounded shadow hover:bg-green-50 focus:border-green-600 focus:outline-green-600 hover:border-green-600 focus:ring-green-600" @change="onChange()" v-model="selected">
      <option value="0">Select Country</option>
      <option v-for="country in countries" :value="country.ID">
      {{ country.Country }}
      </option>
    </select>
  </div>


  



</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);

      this.$emit("get-country", country);
    },
  },
};
</script>
