<template>
<div> 
    <input type="button" value="Сортувати по авторам" @click="sortPhotoByAutors"/>
    <input type="button" value="Сортувати по даті опублікування" @click="sortPhotoByDate"/>
      <ul>
    <photo-template v-for="(b, i) in photo" :key="i" class="photo" v-bind:bk="b"></photo-template>
  </ul>
</div>
</template>

<script>
import photoTemplate from './photoTemplate.vue';
import storage from '../storage';

export default{
    name:"Zavd3", 
    components:{
      photoTemplate,
      
    },
    data(){
      return {
        photo:storage.photo,
      }
    },
     methods: {
    sortPhotoByAutors(){
      this.photo.sort((photo1, photo2) =>  photo1.author>photo2.author?1:-1);
    },
    sortPhotoByDate(){
        this.photo.sort((photo1, photo2) =>  photo1.date>photo2.date?1:-1);
    }
     }
};
</script>