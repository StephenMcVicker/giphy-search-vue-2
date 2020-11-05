<template lang="pug">
  form
    label(for="search") Search Giphy
    input(id="search" placeholder="What gifs do you want to look at?" v-model="keyword" @input="onInput")
</template>

<script>
export default {
  data() {
    return {
      keyword: '',
      timeout: null
    }
  },
  methods: {
    onInput () {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.search();
      }, 500);
    },
    search () {
      console.log("API Key is: " + process.env.VUE_APP_GIPHY_API_KEY);
      fetch (`https://api.giphy.com/v1/gifs/search?api_key=${process.env.VUE_APP_GIPHY_API_KEY}&q=${this.keyword}&limit=12`)
      .then(response => response.json())
      .then(res => {
        console.log(res);
        this.$emit('fetch-gifs', res.data);
      })
    }
  },
}

</script>

<style lang="scss" scoped>
@import "../assets/constants.scss";

  form {
    align-items: flex-start;
    display: flex;
    flex-direction: column;
    margin-bottom: 3rem;
    padding: 0 0 0 1rem;
  }

  input {
    border: 2px solid $primary-font-color;
    border-radius: 4px;
    font-size: 1.2rem;
    margin-top: .5rem;
    outline: none;
    padding: 1rem;
    width: 85%;

    &:focus {
      border-color: $green;
    }
  }

  label {
    font-weight: 900;

    &::first-letter {
      color: $green;
      font-size: 1.5rem;
    }
  }

  @media (min-width: $screen-break-large) {
    input {
      width: 40%;
    }
  }
</style>