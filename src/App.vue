<template>
  <div id="main-app" class="container">
    <div class="row">
      <SearchBar
        :myKey="filterKey"
        :myDir="filterDir"
        @search="searchRecords"
        @request-key="changeKey"
        @request-dir="changeDir"
      />
      <RecordCard :records="filteredRecords" />
    </div>
  </div>
</template>

<script>
import RecordCard from "./components/RecordCard";
import SearchBar from "./components/SearchBar";
import _ from "lodash";

export default {
  data: function () {
    return {
      records: [],
      searchTerms: "",
      filterKey: "title",
      filterDir: "asc"
    };
  },
  components: {
    RecordCard,
    SearchBar,
  },
  mounted() {
    fetch("https://drmusicrestservice.azurewebsites.net/api/DRMusicRecord")
      .then((response) => response.json())
      .then((data) => {
        this.records = data;
      });
  },
  computed: {
    searchedRecords: function () {
      return this.records.filter((item) => {
        return (
          item.title.toLowerCase().match(this.searchTerms.toLowerCase()) ||
          item.artist.toLowerCase().match(this.searchTerms.toLowerCase()) ||
          item.album.toLowerCase().match(this.searchTerms.toLowerCase())
        );
      });
    },
    filteredRecords: function() {
      return _.orderBy(
        this.searchedRecords, item => {
          console.log(this.filterKey);
          return item[this.filterKey].toLowerCase();
        },
        this.filterDir
      );
    }
  },
  methods: {
    searchRecords: function (searchTerm) {
      this.searchTerms = searchTerm;
    },
    changeKey: function (value) {
      this.filterKey = value;
    },
    changeDir: function ( value) {
      this.filterDir = value;
    }
  },
};
</script>
