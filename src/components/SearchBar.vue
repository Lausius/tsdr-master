<template>
  <div class="col-12 col-md-10 col-lg-7">
    <div class="input-group my-3">
      <input
        id="SearchRecords"
        placeholder="Search"
        type="text"
        class="form-control"
        aria-label="Search Appointments"
        v-model="searchTerm"
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      filters: "",
      searchTerm: "",
    };
  },
  watch: {
    searchTerm: function () {
      this.$emit("search", this.searchTerm);
    }
  },
};
</script>

