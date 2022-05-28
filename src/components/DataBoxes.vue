<template>
  <div class="flex flex-col items-center justify-center mx-5 mt-10 space-y-5 text-gray-800 sm:text-xl sm:mx-0">
    <div class="w-full space-y-5 sm:space-x-3 sm:space-y-0 sm:flex sm:h-36">

      <div class="flex flex-col items-center justify-center w-full py-4 bg-green-400 rounded-md shadow-md px-7">
        <div class="text-sm">{{ stats.Country }}</div>
        <div>Coronavirus Cases</div>
        <div>{{ numberWithCommas(stats.TotalConfirmed) }}</div>
      </div>
    
      <div class="flex flex-col items-center justify-center w-full py-4 bg-red-400 rounded-md shadow-md px-7">
        <div class="text-sm">{{ stats.Country }}</div>
        <div>Coronavirus Deaths</div>
        <div>{{ numberWithCommas(stats.TotalDeaths) }}</div>

      </div>

    </div>
   
    <div class="w-full space-y-5 sm:space-x-3 sm:space-y-0 sm:flex">

       <div class="flex flex-col w-full text-gray-900 cursor-pointer">
        <div v-on:click="showNewCases=!showNewCases" 
            class="flex items-center justify-between px-3 py-2 bg-green-300 rounded-sm shadow-sm">
            <div class="opacity-0">
              right
            </div>
            <div class="flex justify-center">New Cases</div>
            <div v-bind:class="{'rotate-180': showNewCases}" class="duration-500 transform">
              <svg
                  class="w-8 h-8"
                  xmlns="http://www.w3.org/2000/svg" 
                  viewBox="0 0 20 20">
                  <path class="fill-current" d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
              </svg>
            </div>
      
        </div>
        <transition
          enter-active-class="duration-300 ease-linear"
          enter-from-class="transform -translate-y-3 opacity-0"
          enter-to-class="opacity-100"
          leave-active-class="duration-150 ease-in"
          leave-from-class=""
          leave-to-class="transform -translate-y-3 opacity-0"
        >
          <div v-if="showNewCases" class="items-center w-full py-6 bg-green-200 top-12">
            <div class="flex items-center justify-center">
              {{ numberWithCommas(stats.NewConfirmed) }}
            </div>
          </div>
        </transition>
      
    </div>

      <div class="flex flex-col w-full text-gray-900 cursor-pointer">
        <div v-on:click="showNewDeaths=!showNewDeaths" 
            class="flex items-center justify-between px-3 py-2 bg-red-300 rounded-sm shadow-sm">
            <div class="opacity-0">
              right
            </div>
            <div class="flex justify-center">New Deaths</div>
            <div v-bind:class="{'rotate-180': showNewDeaths}" class="duration-500 transform">
              <svg
                  class="w-8 h-8"
                  xmlns="http://www.w3.org/2000/svg" 
                  viewBox="0 0 20 20">
                  <path class="fill-current" d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/>
              </svg>
            </div>
      
        </div>
        <transition
          enter-active-class="duration-300 ease-linear"
          enter-from-class="transform -translate-y-3 opacity-0"
          enter-to-class="opacity-100"
          leave-active-class="duration-150 ease-in"
          leave-from-class=""
          leave-to-class="transform -translate-y-3 opacity-0"
        >
          <div v-if="showNewDeaths" class="w-full py-6 bg-red-200 top-12">
            <div class="flex flex-col items-center justify-center">
              {{ numberWithCommas(stats.NewDeaths) }}
            </div>
          </div>
        </transition>
      
    </div>


    </div>
     

  </div>
</template>

<script>

export default {
  name: "DataBoxes",
  props: ["stats"],
  data() {
    return {
      showNewCases:false,
      showNewDeaths:false,
    };
  },
  methods: {
    numberWithCommas(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
