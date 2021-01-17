<template>
  <div>
    <h1>The Guardian</h1>
    <input placeholder="Search for a headline" v-model="searchTerm"></input>
    <button @click="handleSearch">Search</button>
    <ul>
      <NewsItem :news="news"> </NewsItem>
    </ul>
  </div>
</template>

<script>
import NewsItem from "./NewsItem.vue";

export default {
  name: "NewsList",

  data() {
    return {
      news: [],
      searchTerm: "",
    };
  },

  components: {
    NewsItem,
  },

  methods: {
    handleSearch() {
      console.log("Button is clicked, Search term: ", this.searchTerm);

      window
        .fetch(
          `https://content.guardianapis.com/search?q=${this.searchTerm}&format=json&api-key=test&show-fields=body`
        )
        .then((response) => {
          response.json().then((json) => {
            this.news = json.response.results;
            console.log(json.response.results)
          });
        });
    },
  },

  mounted() {
    window
      .fetch(
        "https://content.guardianapis.com/search?q=covid&format=json&api-key=test&show-fields=body"
      )
      .then((response) => {
        response.json().then((json) => {
          this.news = json.response.results;
          console.log(this.news);
        });
      });
  },
};
</script>