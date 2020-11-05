<template lang="pug">
  #app
    gif-search(@fetch-gifs="onFetch")
    gif-list(:gifs="gifs")
    footer
      p Created by Stephen McVicker
      p View source on {{' '}}
        a(href="https://github.com/StephenMcVicker/giphy-search-vue-2"
          target="_blank"
          rel="noopener noreferrer") Github
</template>

<script>

import GifList from "./components/GifList";
import GifSearch from "./components/GifSearch";

export default {
  name: 'App',
  components:{GifList, GifSearch},
  data() {
    return {
      gifs: []
    }
  },
  methods: {
    onFetch(result){
      this.gifs = result;
    }
  }
}
</script>

<style lang="scss">

@import "./assets/constants.scss";

#app {
  color: $primary-font-color;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;

  ::selection{
    background: $green-light;
  }
}

/* * * * * * */
/* Styled scroll bars */
::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 6px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: $green;
  border-radius: 50vh;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: $green-light;
}

/* * * * * * */
</style>
