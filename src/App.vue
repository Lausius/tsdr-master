<template>
  <div id="main-app" class="container">
    <div class="row">
      <SearchBar @search="searchRecords" />
      <RecordCard :records="searchedRecords" />
    </div>
  </div>
</template>

<script>
import RecordCard from "./components/RecordCard";
import SearchBar from "./components/SearchBar";

export default {
  data: function () {
    return {
      records: [],
      searchTerms: "",
    };
  },
  components: {
    RecordCard,
    SearchBar,
  },
  mounted() {
        fetch("https://drmusicrestservice.azurewebsites.net/api/DRMusicRecord")
      .then(response => response.json())
      .then(data => {
        this.records = data;
      });
  },
  computed: {
    searchedRecords: function () {
      return this.records.filter(item => {
        return (
          item.title.toLowerCase().match(this.searchTerms.toLowerCase()) ||
          item.artist.toLowerCase().match(this.searchTerms.toLowerCase()) ||
          item.album.toLowerCase().match(this.searchTerms.toLowerCase())
        );
      });
    },
  },
  methods: {
    searchRecords: function(searchTerm) {
      this.searchTerms = searchTerm;
    },
  },
};
</script>
