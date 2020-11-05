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
      />

      <div class="input-group-append">
        <button
          type="button"
          class="btn btn-primary dropdown-toggle"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
        >
          Sort by
          <span class="caret"></span>
        </button>

        <div class="dropdown-menu dropdown-menu-right">
          <a
            href="#"
            class="dropdown-item d-flex justify-content-between"
            id="title"
            @click="$emit('request-key', 'title')"
          >
            Title
            <div>*</div>
          </a>

          <a
            class="dropdown-item d-flex justify-content-between"
            href="#"
            id="artist"
            @click="$emit('request-key', 'artist')"
          >
            Artist
            <div>*</div>
          </a>

          <a
            href="#"
            class="dropdown-item d-flex justify-content-between"
            id="album"
            @click="$emit('request-key', 'album')"
          >
            Album
            <div v-if="myKey == 'album'">*</div>
          </a>

          <div class="dropdown-divider" role="separator"></div>

          <a
            class="dropdown-item d-flex justify-content-between"
            href="#"
            id="asc"
            @click="$emit('request-dir', 'asc')"
          >
            Asc
            <div v-if="myDir === 'asc'">*</div>
          </a>

          <a
            class="dropdown-item d-flex justify-content-between"
            href="#"
            id="desc"
            @click="$emit('request-dir', 'desc')"
          >
            Desc
            <div v-if="myDir === 'desc'">*</div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchTerm: "",
    };
  },
  watch: {
    searchTerm: function () {
      this.$emit("search", this.searchTerm);
    },
    props: ["myKey", "myDir"],
  },
};
</script>

