<template>
  <main id="app">
    <Hero v-bind:songs="songs" />
    <h1>Hello</h1>
  </main>
</template>

<script>
import Hero from "./components/Hero.vue";

export default {
  data() {
    return {
      songs: [],
    };
  },
  components: {
    Hero,
  },
  async created() {
    this.songs = await this.getSongs();
  },
  methods: {
    getSongs: async () => {
      const query = `{
        blogPostCollection {
          items {
            title
            description
            heroImage {
              url
            }
          }
        }
      }`;
      const fetchUrl = `https://graphql.contentful.com/content/v1/spaces/${process.env.VUE_APP_CONTENTFUL_SPACE_ID}`;
      const fetchOptions = {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.VUE_APP_CONTENTFUL_ACCESS_TOKEN}`,
          "Content-Type": "application/json",
        },
        body: JSON.stringify({ query }),
      };

      try {
        const response = await fetch(fetchUrl, fetchOptions).then((response) =>
          response.json()
        );
        console.log(response.data.blogPostCollection.items);
        return response.data.blogPostCollection.items;
      } catch (error) {
        throw new Error("Could not receive the data from Contentful!");
      }
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/styles/variables.scss";

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: "Verdana";
  background-color: $green;
  color: $black;
}

#app {
  background-color: $green;
  border: 7px solid $black;
  box-shadow: 10px 10px 0 $black;
  border-radius: 7px 7px 7px 0;
  max-width: 1200px;
  margin: 50px auto;
  @media screen and (max-width: 1200px) {
    margin: 20px;
  }
}

ul {
  margin: 0;
  list-style: none;
  padding: 0;
  li {
    display: inline-block;
  }
}
</style>
