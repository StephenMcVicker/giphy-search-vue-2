<template lang="pug">
  figure
    img(:src="gif.images.original.url")
    figcaption Embed URL: 
    input(ref="url" type="text" :value="gif.embed_url")
    button(@click="copyURL") Copy
</template>

<script>
export default {
 props:{
   gif: Object
 },
 methods: {
   copyURL () {
     this.$refs.url.select();
     document.execCommand("copy");
   }
 },
}
</script>

<style lang="scss" scoped>
@import "../assets/constants.scss";

figure {
  display: flex;
  flex-direction: column;
  margin: 1rem;
  padding: 0;

  img {
    height: 200px;
  }

  figcaption {
    color: $purple;
    margin: 0.4rem 0;
    overflow-x: auto;

    input {
      color: $primary-font-color;
      margin: 0.3rem 0;
    }
  }
}

button {
  background: transparent;
  border: 1.5px solid $green;
  border-radius: 4px;
  font-weight: bold;
  margin-top: .5rem;
  outline: none;
  padding: .5rem 1rem;
  text-transform: uppercase;
  transition: all 0.2s;

  &:hover {
    background: $green;
    color: white;
  }
}

</style>