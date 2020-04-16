<template>
  <div id="demo">
    <header>
      Image Gallery
      <div class="description">
        {{ description }}
      </div>
    </header>
    <div class="container">
     <img class="image" v-for="image of galleryPhotos" :key="image.id" :src="image" v-bind:style="{ width: width + 'px', height: height + 'px'}" />
    </div>
  </div>
</template>

<script>
  export default {
    beforeMount: function() {
      this.getPhotos()
    },
    data() {
      return {
        description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci assumenda consectetur, debitis dignissimos fuga, harum illo nesciunt nostrum nulla quisquam rem repellat, soluta vel. Cupiditate deserunt laudantium omnis quos sit.',
        height: 500,
        width: 400,
        numberOfPhotos: 20,
        photos: []
      }
    },
    methods: {
      getPhotos: function() {
        const photosToDisplay = this.numberOfPhotos;
        const photoHeight = this.height;
        const photoWidth = this.width;
        const photos = [];
        for (let i = 0; i < photosToDisplay; i++) {
          photos.push(`https://picsum.photos/${photoWidth}/${photoHeight}?random?id=${i}`);
        }
        this.photos = photos;
      }
    },
    computed: {
      galleryPhotos() { return this.photos }
    }
  };
</script>

<style lang="scss" scoped>

  $main-bg: #f3f3f3;
  $image-container-bg: #fefefe;
  $font-main: Arial;

  body {
    margin: 0;
    font-size: 10px;
  }

  #demo {
      display: flex;
      flex-direction: column;
      justify-content: center;
      text-align: center;
      font-family: $font-main;
      background: $main-bg;
      padding: 4rem;
      align-items: center;

      div {
        &:not(:last-child) {
          margin-bottom: 3rem;
        }
      }
  }

  header {
      font-size: 3rem;
      font-weight: bold;
      margin: 15px;
      .description {
        margin: 15px;
        font-size: 1rem;
        font-weight:300;
      }
  }

  .container {
      background: $image-container-bg;
      box-shadow: 0 1px 2px rgba(34, 25, 25, 0.4);
      margin: 2px 15px;
      padding: 15px;
      padding-bottom: 10px;
      display: inline-block;
      break-inside: avoid;
      column-width: 320px;
      column-gap: 15px;
      width: 90%;
      max-width: 1100px;
      margin: 20px auto;

      .image {
        padding-bottom: 15px;
        margin-bottom: 5px;
      }
  }

</style>
