<!-- eslint-disable vue/no-use-v-if-with-v-for,vue/no-confusing-v-for-v-if -->
<template>
  <div class="container">
    <div class="row">
      <div class="col-6" v-for="item in records" :key="item.id">
        <div class="card">
          <div class="card-body text-center">
            <h2 class="card-header ">{{ item.title }}</h2>
            <img
              class="card-img img-responsive mt-1 rounded"
              v-if="item.artist === 'Michael Jackson'"
              src="../assets/Michael.jpg"
            />
            <img
              class="card-img img-responsive mt-1 rounded"
              v-else-if="item.artist === 'Justin Bieber'"
              src="../assets/JustinBieber.jpg"
            />
            <img
              class="card-img img-responsive mt-1 rounded"
              v-else-if="item.artist === 'Justin Timberlake'"
              src="../assets/Timberlake.jpg"
            />
            <p class="card-text lead">
              <strong> Artist:</strong> {{ item.artist }}
            </p>
            <p class="lead">Album: {{ item.album }}</p>
            <p class="lead">Publication year: {{ item.yearOfPublication }}</p>
            <p class="lead">Duration: {{ item.duration }} seconds</p>
            <a href="#!" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
      <!-- col -->
    </div>
    <!-- row -->
  </div>
  <!-- container -->
</template>

<script lang="ts">
import Vue from "vue";

export default {
  name: "RecordCard",
  props: ["records"],
  components: {},
  };
</script>

<style scoped></style>
