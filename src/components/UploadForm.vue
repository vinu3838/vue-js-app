<template>
<div>
    <div class="dropper" v-if="isLoggedIn">
        <input type="file" 
        multiple
        accept= "images/*"
        @change="uploadImages($event.target.files)"/>
        <span>Drop files here!</span>
    </div>
    <h2 v-else>
      Log in to get started
  </h2>
</div>
</template>
<script>
import {mapActions, mapGetters} from 'vuex';
export default {
    name:'UploadForm',
    methods: {
        ...mapActions(['uploadImages'])
    },
    computed: {
         ...mapGetters(["isLoggedIn"]),
    }
}
</script>
<style scoped>
.dropper {
    height: 30vh;
    border: 2px dashed black;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    position:relative;
}
.dropper:hover {
    background-color: #eee;
    cursor:pointer;
}
input {
    width: 100%;
    height: 30vh;
    position:absolute;
    opacity: 0;
}
</style>