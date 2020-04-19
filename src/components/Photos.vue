<template>
  <div class="component-wrapper">
    <header class="header">
      <h2 class="header__title">
        {{ title }}
      </h2>
      <p class="header__description">
        {{ description }}
      </p>
    </header>
    <div class="gallery">
      <img class="gallery__image" v-for="item in this.photoSources" :src="item" alt="item" :key="item" :style="{ height: height + 'px', width: width + 'px' }" />
    </div>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  // eslint-disable-next-line no-unused-vars
  import { GalleryData }  from '../types';

  export default Vue.extend({
    name: 'Photos',
    beforeMount(): void {
      this.getPhotos()
    },
    data(): GalleryData {
      return {
        title: 'Image Gallery',
        description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci assumenda consectetur, debitis dignissimos fuga, harum illo nesciunt nostrum nulla quisquam rem repellat, soluta vel. Cupiditate deserunt laudantium omnis quos sit.',
        height: 300,
        width: 300,
        numberOfPhotos: 18,
        photoSources: []
      }
    },
    methods: {
      getPhotos(): void {
        const photosToDisplay = this.numberOfPhotos;
        const photoHeight = this.height;
        const photoWidth = this.width;
        const photos: string[] = [];
        for (let i = 0; i < photosToDisplay; i++) {
          photos.push(`https://picsum.photos/${photoWidth}/${photoHeight}?random&id=${i}`);
        }
        this.photoSources = photos;
      }
    }
  });
</script>

<style lang="scss">
  $main-bg: #f3f3f3;
  $image-container-bg: #fefefe;
  $font-main: Arial;

  body {
    margin: 0;
    font-size: 10px;
  }

  .component-wrapper {
    font-family: $font-main;
    background: $main-bg;
    padding: 4rem;
    max-width: 1100px;
    div {
      &:last-child {
        margin-bottom: 0rem;
      }
    }
  }

  .header {    
    margin: 10px auto;
    padding: 15px;
    text-align: center;
    &__title {
      font-size: 3rem;
      font-weight: bold;
    }
    &__description {
      font-size: 1.5rem;
      font-weight:300;
    }
  }

  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    background-color: $image-container-bg;
    box-shadow: 0 1px 2px rgba(34, 25, 25, 0.4);
    margin: 2px 15px;
    padding: 15px;
    &__image {
      margin: 5px;
    }
  }
</style>
