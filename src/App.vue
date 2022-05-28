<template>
  <Header />
  <div class="container max-w-xl">
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header";
export default {
  components: {
    Header,
  },
};
</script>
