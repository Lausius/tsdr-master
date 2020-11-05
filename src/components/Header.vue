<template>
  <div>
    <h1 class="border border-dark text-center">
      DR Music
    </h1>
    <SearchBar v-on:change-filter="$emit('change-filter', filters)" />
  </div>
</template>

<script lang="ts">
import component from "*.vue";

import Vue from "vue-class-component";
import SearchBar from "./SearchBar.vue";
export default {
  name: "Header",
  components: { SearchBar },
};
</script>
